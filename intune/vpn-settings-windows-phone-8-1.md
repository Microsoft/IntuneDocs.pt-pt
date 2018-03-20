---
title: "Definições de VPN para dispositivos Windows Phone 8.1 no Microsoft Intune"
titleSuffix: 
description: "Saiba mais sobre as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 786a817fbbd821d74f4f1a03fdec5a6893ed890b
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Configurar definições de VPN no Microsoft Intune para dispositivos com o Windows Phone 8.1

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows Phone 8.1.


Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Aplicar todas as definições apenas ao Windows Phone 8.1** – Esta é uma definição que pode configurar no portal clássico do Intune. No portal do Azure, esta definição não pode ser alterada. Se esta definição estiver definida como **Configurada**, as definições só são aplicadas a dispositivos com o Windows Phone 8.1. Se estiver definida como **Não configurada**, estas definições também são aplicadas a dispositivos com o Windows 10 Mobile.
- **Nome da ligação** – Introduza um nome para esta ligação. Os utilizadores verão este nome quando procurarem a lista de ligações VPN disponíveis no dispositivo.
- **Método de autenticação** – escolha como os dispositivos serão autenticados no servidor VPN em:
    - **Certificados** – Em **Certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS que criou anteriormente para autenticar a ligação. Para obter mais detalhes sobre os perfis de certificado, veja [Como configurar certificados](certificates-configure.md).
    - **Nome de utilizador e palavra-passe** – Os utilizadores finais têm de indicar um nome de utilizador e uma palavra-passe para iniciar sessão no servidor VPN.
- **Servidores** – adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
    - **Adicionar** – Abre o painel **Adicionar Linha**, onde pode especificar as seguintes informações:
        - **Descrição** – Especifique um nome descritivo para o servidor, como **Servidor VPN Contoso**.
        - **Endereço IP ou FQDN** – forneça o endereço IP ou nome de domínio completamente qualificado do servidor VPN ao qual os dispositivos são ligados. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predefinido** – define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
    - **Importar** – Navegue até um ficheiro que contenha uma lista separada por vírgulas de servidores no formato descrição, endereço IP ou FQDN, Servidor predefinido. Escolha **OK** para importá-los para a lista **Servidores**.
    - **Exportar** – Exporta a lista de servidores para um ficheiro de valores separados por vírgulas (csv).

- **Ignorar VPN na rede Wi-Fi da empresa** – ative esta opção para especificar que as ligações VPN não são utilizadas quando o dispositivo estiver ligado à rede Wi-Fi da empresa.
- **Ignorar VPN na rede Wi-Fi doméstica** – ative esta opção para especificar que a ligação VPN não é utilizada quando o dispositivo estiver ligado à rede Wi-Fi doméstica.

- **Tipo de ligação** – selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
    - **Check Point Capsule VPN**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Grupo ou domínio de início de sessão** (apenas no SonicWall Mobile Connect) – especifique o nome do grupo ou domínio de início de sessão ao qual se pretende ligar.
- **Função** (apenas no Pulse Secure) – Especifique o nome da função de utilizador que tem acesso a esta ligação. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.
- **Realm** (apenas no Pulse Secure) – Especifique o nome do realm de autenticação que pretende utilizar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.

- **Lista de pesquisa de sufixos DNS** - **Adicionar** um ou mais sufixos DNS. Cada sufixo DNS especificado é procurado ao ligar-se a um site com um nome abreviado. Por exemplo, especifique os sufixos DNS **dominio1.contoso.com** e **dominio2.contoso.com**, aceda ao URL **http://omeuwebsite** e os URLs **http://omeuwebsite.dominio1.contoso.com** e **http://omeuwebsite.dominio2.contoso.com** são procurados.

- **XML personalizado** – Especifique todos os comandos XML personalizados que configuram a ligação VPN.

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

Consulte a documentação de cada fabricante relativa à VPN para obter mais informações sobre como escrever comandos XML personalizados.

- **Dividir túnel** - **Ative** ou **Desative** esta opção para permitir que os dispositivos decidam qual a ligação a utilizar consoante o tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.




## <a name="proxy-settings"></a>Definições de proxy

- **Detetar automaticamente as definições de proxy** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, especifique se quer que os dispositivos detetem automaticamente as definições de ligação. Para mais informações, veja a documentação do Windows Server.
- **Script de configuração automática** – Utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, **http://proxy.contoso.com**) que contém o ficheiro de configuração.
- **Utilizar um servidor proxy** – Ative esta opção se quiser introduzir manualmente as definições do servidor proxy.
    - **Endereço** – Introduza o endereço do servidor proxy (como um endereço IP).
    - **Número de porta** – Introduza o número de porta associado ao servidor proxy.
- **Ignorar o proxy para endereços locais** – Se o seu servidor VPN precisar de um servidor proxy para a ligação, selecione esta opção caso não pretenda utilizar o servidor proxy para endereços locais especificados. Para mais informações, veja a documentação do Windows Server.
