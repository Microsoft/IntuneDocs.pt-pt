---
title: Definições de VPN do Microsoft Intune para dispositivos com o Windows 8.1
titleSuffix: ''
description: Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 521243d2c6560fbac77a4ee2aba6ed9577d3abe1
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "71303246"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Configurar definições de VPN no Microsoft Intune para dispositivos com o Windows 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows 8.1.

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base


- **Aplicar todas as definições apenas ao Windows 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só são aplicadas a dispositivos com o Windows 8.1. Se estiver definida como **Não configurada**, estas definições também são aplicadas a dispositivos com o Windows 10.
- **Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores verão este nome quando procurarem a lista de ligações VPN disponíveis no dispositivo.
- **Servidores** – adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
  - **Adicionar** – abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
    - **Descrição** – Especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
    - **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
    - **Servidor predefinido** – define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
  - **Importar** – Navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
  - **Exportar** – Exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo ou domínio de início de sessão** (apenas no SonicWall Mobile Connect) – especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.

- **Função** (apenas no Pulse Secure) – Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.

- **Realm** (apenas no Pulse Secure) – Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.


- **XML personalizado** – Especifique todos os comandos XML personalizados que configuram a ligação VPN.

**Exemplo para o Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exemplo para o CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exemplo para o SonicWall Mobile Connect:**

```xml
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exemplo para o F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obter mais informações, consulte a documentação de cada fabricante relativa à VPN sobre como escrever comandos XML personalizados.


## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, veja a documentação do Windows Server.
- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy**, que contém o ficheiro de configuração. Por exemplo, introduza `http://proxy.contoso.com`.
- **Utilizar um servidor proxy** – Ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
  - **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
  - **Número de porta** – Introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, veja a documentação do Windows Server.
