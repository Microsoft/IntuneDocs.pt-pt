---
title: "Definições de VPN do Intune para dispositivos Windows 8.1"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos Windows 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: f38526a3e60f2a6628e61ffca5f5d179a2718e9b


---

# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos Windows 8.1 no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base


- **Aplicar todas as definições apenas ao Windows 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10.
- **Nome da ligação** – introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Servidores** – adicione um ou mais servidores VPN aos quais os dispositivos serão ligados.
    - **Adicionar** – abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – indique o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – ativa este servidor como o servidor predefinido que os dispositivos vão utilizar para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
    - **Importar** – Navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – Exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo ou domínio de início de sessão** (apenas no Dell SonicWALL Mobile Connect) – especifique o nome do grupo ou domínio de início de sessão ao qual pretende estabelecer ligação.

- **Função** (apenas no Pulse Secure) – Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.

- **Realm** (apenas no Pulse Secure) – Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.


- **XML personalizado** – Especifique todos os comandos XML personalizados que configuram a ligação VPN.

**Exemplo para o Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**Exemplo para o CheckPoint Mobile VPN:**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />

```

**Exemplo para o Dell SonicWALL Mobile Connect:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Exemplo para o F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Consulte a documentação de cada fabricante relativa à VPN para obter mais informações sobre como escrever comandos XML personalizados.


## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, consulte a documentação do Windows Server.
- **Script de configuração automática** – utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para os endereços locais especificados. Para mais informações, consulte a documentação do Windows Server.



<!--HONumber=Feb17_HO3-->


