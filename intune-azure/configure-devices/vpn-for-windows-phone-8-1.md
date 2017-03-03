---
title: "Definições de VPN do Intune para dispositivos Windows Phone 8.1 | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba mais sobre as definições do Intune que pode utilizar para configurar ligações de VPN em dispositivos Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 674a806b16d1f88413c1d1bbda1fb1d4f3363771
ms.lasthandoff: 02/16/2017


---

# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Definições de VPN para dispositivos Windows Phone 8.1 no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Consoante as definições que escolher, nem todos os valores na lista abaixo serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só serão aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também serão aplicadas a dispositivos com o Windows 10 Mobile.
- **Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores finais verão este nome quando procurarem no dispositivo a lista de ligações VPN disponíveis.
- **Método de autenticação** – Escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Em **Certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](how-to-configure-certificates.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Servidores** – Adicione um ou mais servidores VPN aos quais os dispositivos serão ligados.
    - **Adicionar** – Abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – Especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – Forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos serão ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – Ativa este servidor como o servidor predefinido que os dispositivos vão utilizar para estabelecer a ligação. Confirme que predefine apenas um servidor.
    - **Importar** – Navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – Exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

- **Ignorar VPN na rede Wi-Fi da empresa** – Ative esta opção para especificar que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi da empresa.
- **Ignorar VPN na rede Wi-Fi doméstica** – Ative esta opção para especificar que a ligação VPN não será utilizada quando o dispositivo estiver ligado à rede Wi-Fi doméstica.

- **Tipo de ligação** – Selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Grupo ou domínio de início de sessão** (apenas no Dell SonicWALL Mobile Connect) – Especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.
- **Função** (apenas no Pulse Secure) – Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.
- **Realm** (apenas no Pulse Secure) – Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.

- **Lista de pesquisa de sufixos DNS** - **Adicionar** um ou mais sufixos DNS. Cada sufixo DNS especificado será procurado ao ligar-se a um site com um nome abreviado. Por exemplo, especifique os sufixos DNS **dominio1.contoso.com** e **dominio2.contoso.com**, aceda ao URL **http://omeuwebsite** e os URLs **http://omeuwebsite.dominio1.contoso.com** e **http://omeuwebsite.dominio2.contoso.com serão procurados**.

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

- **Divisão de túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utilizará a ligação VPN para aceder aos ficheiros de trabalho, mas utilizará a rede padrão do hotel para a navegação normal na Internet.




## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, consulte a documentação do Windows Server.
- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – Ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – Introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, consulte a documentação do Windows Server.

