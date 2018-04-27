---
title: Definições de Wi-Fi do Microsoft Intune para dispositivos macOS
titleSuffix: ''
description: Conheça as definições do Intune que pode utilizar para configurar ligações Wi-Fi em dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81bd3cb54a1490732083b52a1fe242146183eebc
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="wi-fi-settings-for-macos-devices-in-microsoft-intune"></a>Definições de Wi-Fi para dispositivos macOS no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra-lhe as definições de Wi-Fi que pode configurar no Microsoft Intune para dispositivos macOS.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Definições de Wi-Fi para perfis básicos e empresariais

- **Nome da rede** – Introduza um nome para esta ligação Wi-Fi. Este é o nome que os utilizadores veem quando navegam na lista de ligações disponíveis nos respetivos dispositivos.
- **SSID** – Sigla de Service Set Identifier (identificador do conjunto de serviço). Este é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores apenas veem o nome da rede configurada por si quando selecionam a ligação.
- **Ligar automaticamente** – Faz com que o dispositivo se ligue sempre que estiver ao alcance desta rede.
- **Rede oculta** – Impede que esta rede seja apresentada na lista de redes disponíveis no dispositivo.
- **Definições de proxy** – Escolha entre:
    - **Nenhuma** – Não são configuradas definições de proxy.
    - **Manual** – Introduza o **Endereço de servidor proxy** (como um endereço IP) e o **Número de porta** associado.
    - **Automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Definições de Wi-Fi apenas para perfis básicos

- **Tipo de segurança** – Selecione o protocolo de segurança que vai servir para autenticar a rede Wi-Fi entre:
    - **Aberto (sem autenticação)** – Utilize esta opção apenas se a rede não for protegida.
    - **WPA/WPA2 – Pessoal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Definições de Wi-Fi apenas para perfis empresariais

- **Tipo de EAP** – Selecione o tipo Protocolo EAP (Extensible Authentication Protocol) que serve para autenticar as ligações sem fios protegidas entre:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Outras opções ao selecionar um tipo de EAP


|Nome da definição|Mais informações|Utilizar quando|
|--------------|-------------|----------|
|**Definições de PAC (Credencial de Acesso Protegido)**|Selecione para utilizar credenciais de acesso protegido para estabelecer um túnel autenticado entre o cliente e o servidor de autenticação. Selecione uma das opções:<br>- **Utilizar PAC** – Se já existir um ficheiro PAC, este será utilizado.<br>- **Utilizar e Aprovisionar PAC** – Aprovisione o ficheiro PAC para os seus dispositivos.<br>- **Aprovisionar PAC Anonimamente** – Aprovisione o ficheiro PAC para os seus dispositivos e confirme que o ficheiro PAC é aprovisionado sem autenticar o servidor.|O tipo de EAP é **EAP-FAST**|

#### <a name="server-trust"></a>Fidedignidade do Servidor


|Nome da definição|Mais informações|Utilizar quando|
|--------------|-------------|----------|
|**Nomes de servidores de certificados**|Especifique um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Se indicar estas informações, pode ignorar a caixa de diálogo de confiança dinâmica que é apresentada em dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.|O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**.|
|**Certificado de raiz para a validação do servidor**|Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação. |O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**|
|**Privacidade de identidade (identidade externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O tipo de EAP é **PEAP**|


#### <a name="client-authentication"></a>Autenticação de Cliente


|                                     Nome da definição                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Mais informações                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Utilizar quando                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Certificado de cliente para autenticação de cliente (Certificado de identidade)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Escolha o perfil de certificado SCEP ou PKCS que serve para autenticar a ligação.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              O tipo de EAP é <strong>EAP-TLS</strong>              |
|                        <strong>Método de autenticação</strong>                        | Selecione o método de autenticação da ligação:<br>- <strong>Certificados</strong> para selecionar a SCEP ou PKCS do certificado de cliente que é o certificado de identidade apresentado para o servidor.<br><br>- <strong>Nome de utilizador e Palavra-passe</strong> para especificar um método de autenticação diferente. <br><br>Se tiver selecionado <strong>Nome de utilizador e Palavra-passe</strong>, configure:<br><br>-  <strong>Método não EAP (identidade interna)</strong> e, em seguida, selecione a forma como autentica a ligação entre:<br>- <strong>Nenhum</strong><br>- <strong>Palavra-passe não encriptada (PAP)</strong><br>- <strong>Protocolo CHAP (Challenge Handshake Authentication Protocol)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP Versão 2 (MS-CHAP v2)</strong><br>As opções disponíveis dependerão do tipo EAP que selecionou.<br><br><strong>e</strong><br><br>- <strong>Privacidade de identidade (identidade externa)</strong> – Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro. | O tipo de EAP é <strong>EAP-TTLS</strong> ou <strong>PEAP</strong> |

