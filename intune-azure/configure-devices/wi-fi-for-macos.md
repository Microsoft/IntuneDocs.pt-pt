---
title: "Definições de Wi-Fi do Intune para dispositivos macOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: conheça as definições do Intune que pode utilizar para configurar ligações Wi-Fi em dispositivos macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 322a38d5-21f5-48ee-bc59-0a4f9da78d38
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac907e4cb63e4175dafc4c50239d3e0cbe581ad9
ms.openlocfilehash: 46c567dbcbfb84d4e0f8e3c3e8567cc6498befcf


---

# <a name="intune-wi-fi-settings-for-macos-devices-in-intune-azure-preview"></a>Definições de Wi-Fi do Intune para dispositivos macOS na pré-visualização do Azure no Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Definições de Wi-Fi para perfis básicos e empresariais

- **Nome da rede** – Introduza um nome para esta ligação Wi-Fi. Este é o nome que será visto pelos utilizadores quando navegam na lista de ligações disponíveis nos dispositivos deles.
- **SSID** – Sigla de Service Set Identifier (identificador do conjunto de serviço). Este é o nome real da rede sem fios à qual os dispositivos se vão ligar. No entanto, os utilizadores apenas veem o nome da rede que criou acima quando selecionam a ligação.
- **Ligar automaticamente** – Faz com que o dispositivo se ligue sempre que estiver ao alcance desta rede.
- **Rede oculta** – Impede que esta rede seja apresentada na lista de redes disponíveis no dispositivo.
- **Definições de proxy** – Escolha entre:
    - **Nenhuma** – Não serão configuradas quaisquer definições de proxy.
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
|**Nomes de servidores de certificados**|Especifique um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) fidedigna. Se indicar estas informações, pode ignorar a caixa de diálogo de confiança dinâmica que é apresentada em dispositivos dos utilizadores finais quando estes se ligam a esta rede Wi-Fi.|O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**.|
|**Certificado de raiz para a validação do servidor**|Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação. |O tipo de EAP é **EAP-TLS**, **EAP-TTLS** ou **PEAP**|
|**Privacidade de identidade (identidade externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O tipo de EAP é **PEAP**|


#### <a name="client-authentication"></a>Autenticação de Cliente


|Nome da definição|Mais informações|Utilizar quando|
|--------------|-------------|----------|
|**Certificado de cliente para autenticação de cliente (Certificado de identidade)**|Escolha o perfil de certificado SCEP ou PKCS que serve para autenticar a ligação.|O tipo de EAP é **EAP-TLS**|
|**Método de autenticação**|Selecione o método de autenticação da ligação:<br>- **Certificados** para selecionar a SCEP ou PKCS do certificado de cliente que é o certificado de identidade apresentado para o servidor.<br><br>- **Nome de utilizador e Palavra-passe** para especificar um método de autenticação diferente. <br><br>Se tiver selecionado **Nome de utilizador e Palavra-passe**, configure:<br><br>-  **Método não EAP (identidade interna)** e, em seguida, selecione a forma como irá autenticar a ligação entre:<br>- **Nenhum**<br>- **Palavra-passe não encriptada (PAP)**<br>- **Protocolo CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Versão 2 (MS-CHAP v2)**<br>As opções disponíveis dependerão do tipo EAP que selecionou.<br><br>**e**<br><br>- **Privacidade de identidade (identidade externa)** – Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O tipo de EAP é **EAP-TTLS** ou **PEAP**|



<!--HONumber=Feb17_HO1-->

