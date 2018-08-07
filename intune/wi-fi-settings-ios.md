---
title: Configurar as definições de Wi-Fi do Microsoft Intune para dispositivos com iOS
titleSuffix: ''
description: Saiba quais são as definições de configuração de Wi-Fi do Intune nos dispositivos com iOS
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
ms.openlocfilehash: 4b723bd23681d98463adae83be5f74b556dc779e
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321157"
---
# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Definições de Wi-Fi para dispositivos iOS no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de Wi-Fi que pode configurar no Microsoft Intune para os dispositivos com iOS.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Definições de Wi-Fi para perfis básicos e empresariais

- **Nome da rede** – introduza um nome para esta ligação Wi-Fi. Este é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos respetivos dispositivos.
- **SSID** – sigla de Service Set Identifier (identificador do conjunto de serviço). Este é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Ligar automaticamente** – faz com que o dispositivo se ligue sempre que estiver ao alcance desta rede.
- **Rede oculta** – impede que esta rede seja apresentada na lista de redes disponíveis no dispositivo.
- **Chave pré-partilhada** - 
- **Definições de proxy** – escolha entre:
    - **Nenhuma** – não são configuradas definições de proxy.
    - **Manual** – introduza o **Endereço de servidor proxy** (como um endereço IP) e o **Número de porta** associado.
    - **Automática** – utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Definições de Wi-Fi apenas para perfis básicos

- **Tipo de segurança** – selecione o protocolo de segurança que vai servir para autenticar a rede Wi-Fi entre:
    - **Aberto (sem autenticação)** – utilize esta opção apenas se a rede não for protegida.
    - **WPA/WPA2 – Pessoal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Definições de Wi-Fi apenas para perfis empresariais

- **Tipo de EAP** – selecione o tipo Protocolo EAP (Extensible Authentication Protocol) que serve para autenticar as ligações sem fios protegidas entre:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Outras opções ao selecionar um tipo de EAP


|Nome da definição|Mais informações|Utilizar quando|
|--------------|-------------|----------|
|**Definições de PAC (Credencial de Acesso Protegido)**|Selecione para utilizar credenciais de acesso protegido para estabelecer um túnel autenticado entre o cliente e o servidor de autenticação. Selecione uma das opções:<br>- **Utilizar PAC** – se já existir um ficheiro PAC, este será utilizado.<br>- **Utilizar e Aprovisionar PAC** – aprovisione o ficheiro PAC para os seus dispositivos.<br>- **Aprovisionar PAC Anonimamente** – aprovisione o ficheiro PAC para os seus dispositivos e confirme que o ficheiro PAC é aprovisionado sem autenticar o servidor.|O tipo de EAP é **EAP-FAST**|

#### <a name="server-trust"></a>Fidedignidade do Servidor


|Nome da definição|Mais informações|Utilizar quando|
|--------------|-------------|----------|
|**Nomes de servidores de certificados**|Especifique um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Se fornecer estas informações, pode ignorar a caixa de diálogo de confiança dinâmica que é apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.|O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**.|
|**Certificado de raiz para a validação do servidor**|Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação. |O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**|
|**Privacidade de identidade (identidade externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O tipo de EAP é **PEAP**|


#### <a name="client-authentication"></a>Autenticação de Cliente


| Nome da definição | Mais informações | Utilizar quando |
|---|---|---|
| **Certificado de cliente para autenticação de cliente (Certificado de Identidade)**** |  Escolha o perfil de certificado SCEP ou PKCS que serve para autenticar a ligação.  |    O tipo de EAP é **EAP-TLS**    |
| **Método de autenticação** | Selecione o método de autenticação da ligação:<br>- **Certificados** para selecionar a SCEP ou PKCS do certificado de cliente que é o certificado de identidade apresentado para o servidor.<br><br>- **Nome de utilizador e Palavra-passe** para especificar um método de autenticação diferente. <br><br>Se tiver selecionado **Nome de utilizador e Palavra-passe**, configure:<br><br>-  **Método não EAP (identidade interna)** e, em seguida, selecione a forma como autentica a ligação entre:<br>- **Nenhum**<br>- **Palavra-passe não encriptada (PAP)**<br>- **Protocolo CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Versão 2 (MS-CHAP v2)**<br>As opções disponíveis dependerão do tipo EAP que selecionou.<br><br>**e**<br><br>- **Privacidade de identidade (identidade externa)** – especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro. | O tipo de EAP é **EAP-TTLS** ou * |

