---
title: Definições de VPN do Microsoft Intune para dispositivos com o Windows 8.1
titleSuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows 8.1.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cbcc3be31a6d9de7ce87ea5b25b8c1a2c42b47cd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Configurar definições de VPN no Microsoft Intune para dispositivos com o Windows 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows 8.1.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base


- **Aplicar todas as definições apenas ao Windows 8.1** – esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só são aplicadas a dispositivos com o Windows 8.1. Se estiver definida como **Não configurada**, estas definições também são aplicadas a dispositivos com o Windows 10.
- **Nome da ligação** – introduza um nome para esta ligação. Os utilizadores verão este nome quando procurarem a lista de ligações VPN disponíveis no dispositivo.
- **Servidores** – adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
    - **Adicionar** – abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
    - **Importar** – navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo ou domínio de início de sessão** (apenas no SonicWall Mobile Connect) – especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.

- **Função** (apenas no Pulse Secure) – especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.

- **Realm** (apenas no Pulse Secure) – especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.


- **XML personalizado** – especifique todos os comandos XML personalizados que configuram a ligação VPN.

**Exemplo para o Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exemplo para o CheckPoint Mobile VPN:**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exemplo para o SonicWall Mobile Connect:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exemplo para o F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obter mais informações, consulte a documentação de cada fabricante relativa à VPN sobre como escrever comandos XML personalizados.


## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para obter mais informações, veja a documentação do Windows Server.
- **Script de configuração automática** – utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para obter mais informações, veja a documentação do Windows Server.
