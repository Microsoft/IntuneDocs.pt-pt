---
title: Definir as configurações de VPN em dispositivos Windows Phone 8,1 no Microsoft Intune-Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de VPN usando as definições de configuração de VPN (rede virtual privada), incluindo os detalhes da conexão e as configurações de proxy para incluir o endereço IP ou FQDN e a porta TCP em Microsoft Intune em dispositivos que executam o Windows Phone 8,1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f33fe132eb6c3dbf91c5dc313369d75f4f3e24
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207031"
---
# <a name="add-vpn-settings-on-windows-phone-81-devices-in-microsoft-intune"></a>Adicionar configurações de VPN em dispositivos Windows Phone 8,1 no Microsoft Intune



Este artigo mostra as definições do Intune que pode utilizar para configurar ligações VPN em dispositivos com o Windows Phone 8.1. 

Consoante as definições que escolher, nem todos os valores na lista seguinte serão configuráveis.

>[!IMPORTANT]
>Windows Phone perfis de VPN 8,1 também são aplicados a dispositivos Windows 10.

## <a name="base-vpn-settings"></a>Definições de VPN Base

- **Aplicar todas as configurações somente a Windows Phone 8,1**: defina essa configuração no portal clássico do Intune. No centro de administração do Microsoft Endpoint Manager, essa configuração não pode ser alterada. Quando definido como **configurado**, todas as configurações são aplicadas somente aos dispositivos Windows Phone 8,1. Quando definido como **não configurado**, essas configurações também se aplicam a dispositivos Windows 10 Mobile.
- **Nome da ligação**: introduza um nome para esta ligação. Os utilizadores verão este nome quando procurarem a lista de ligações VPN disponíveis no dispositivo.
- **Método de autenticação**: escolha como os dispositivos serão autenticados no servidor VPN em:
  - **Certificados**: em **certificado de autenticação**, escolha um perfil de certificado SCEP ou PKCS criado anteriormente para autenticar a conexão. Para obter mais informações sobre os perfis de certificado, veja [Como configurar certificados](../protect/certificates-configure.md).
  - **Nome de usuário e senha**: os usuários finais devem fornecer um nome de usuário e senha para fazer logon no servidor VPN.
- **Servidores**: adicione um ou mais servidores VPN aos quais os dispositivos são ligados.
  - **Adicionar**: abre a folha **Adicionar linha** , na qual você pode especificar as seguintes informações:
    - **Descrição**: especifique um nome descritivo para o servidor, como o **servidor VPN da Contoso**.
    - **Endereço IP ou FQDN**: forneça o endereço IP ou o nome de domínio totalmente qualificado do servidor VPN ao qual os dispositivos se conectam. Exemplos: **192.168.1.1**, **vpn.contoso.com**.
    - **Servidor predefinido**: define este servidor como o servidor predefinido que os dispositivos utilizam para estabelecer a ligação. Certifique-se de que predefine apenas um servidor.
  - **Importar**: Navegue até um arquivo separado por vírgulas com uma lista de servidores no formato descrição, endereço IP ou FQDN, servidor padrão. Escolha **OK** para importar estes servidores para a lista **Servidores**.
  - **Exportar**: exporta a lista de servidores para um arquivo CSV (valores separados por vírgula).

- **Ignorar VPN na rede Wi-Fi da empresa**: Habilite esta opção para especificar que as conexões VPN não serão usadas quando o dispositivo estiver conectado à rede Wi-Fi da empresa.
- **Ignorar VPN na rede Wi-Fi doméstica**: Habilite esta opção para especificar que a conexão VPN não será usada quando o dispositivo estiver conectado a uma rede Wi-Fi doméstica.

- **Tipo de ligação**: selecione o tipo de ligação VPN a partir da seguinte lista de fornecedores:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Grupo de logon ou domínio** (somente SonicWALL Mobile Connect): especifique o nome do grupo de logon ou domínio ao qual você deseja se conectar.
- **Função** (somente Pulse Secure): especifique o nome da função de usuário que tem acesso a essa conexão. Uma função de utilizador define opções e definições pessoais e ativa ou desativa funcionalidades de acesso específicas.
- **Realm** (somente Pulse Secure): especifique o nome do realm de autenticação que você deseja usar. Um realm de autenticação é um agrupamento de recursos de autenticação utilizado pelo tipo de ligação Pulse Secure.

- **Lista de pesquisa de sufixo DNS**: **adicione** um ou mais insuficientes DNS. Cada sufixo DNS especificado é procurado ao ligar-se a um site com um nome abreviado. Por exemplo, especifique os sufixos DNS **domain1.contoso.com** e **domain2.contoso.com**, visite o URL `http://mywebsite` e os URLs `http://mywebsite.domain1.contoso.com` e `http://mywebsite.domain2.contoso.com` são pesquisados.

- **XML personalizado**: especifique qualquer comando XML personalizado que configure a conexão VPN.

  **Exemplo de proteção de pulso**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Exemplo de VPN móvel de ponto de verificação**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **Exemplo do SonicWALL Mobile Connect**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **Exemplo de F5 Edge Client**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Para obter mais informações sobre como escrever comandos XML personalizados, consulte a documentação de VPN do fabricante.

- **Túnel dividido**: **habilite** ou **desabilite** essa opção que permite que os dispositivos decidam qual conexão usar dependendo do tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

## <a name="proxy-settings"></a>Definições de proxy

- **Detectar automaticamente as configurações de proxy**: se o servidor VPN exigir um servidor proxy para a conexão, especifique se deseja que os dispositivos detectem automaticamente as configurações de conexão.
- **Script de configuração automática**: utilize um ficheiro para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que contém o ficheiro de configuração.
- **Usar servidor proxy**: Habilite esta opção se desejar inserir manualmente as configurações do servidor proxy.
  - **Endereço**: Insira o endereço do servidor proxy (como um endereço IP).
  - **Número de porta**: introduza o número de porta associado ao servidor proxy.
- **Ignorar proxy para endereços locais**: se o servidor VPN exigir um servidor proxy para a conexão e você não quiser usar o servidor proxy para endereços locais inseridos, selecione essa opção.

## <a name="next-steps"></a>Próximos passos

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Defina as configurações de VPN em dispositivos [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)e [Windows 10](vpn-settings-windows-10.md) .
