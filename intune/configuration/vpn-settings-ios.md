---
title: Definir configurações de VPN para dispositivos iOS no Microsoft Intune-Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de VPN com definições de rede privada virtual (VPN), incluindo os detalhes da ligação, os métodos de autenticação e a divisão de túnel nas definições base; as definições de VPN personalizadas com o identificador e os pares de valor e chave; as definições de VPN por aplicação que incluem URLs do Safari e VPNs a pedido com SSIDs ou domínios de pesquisa DNS; e as definições de proxy para incluir um script de configuração, endereço IP ou FQDN e porta TCP no Microsoft Intune em dispositivos iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 274b5a8d45f9fb525010e4d225172a6a1ce22275
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730460"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Adicionar configurações de VPN em dispositivos iOS no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Microsoft Intune inclui várias definições de VPN que podem ser implementadas nos seus dispositivos iOS. Estas definições são utilizadas para criar e configurar ligações VPN à rede da sua organização. Este artigo descreve estas definições. Algumas definições só estão disponíveis para alguns clientes VPN, tais como o Citrix, Zscaler, entre outros.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](vpn-settings-configure.md).

> [!NOTE]
> Essas configurações estão disponíveis para todos os tipos de registro. Para obter mais informações sobre os tipos de registro, consulte [registro do IOS](../enrollment/ios-enroll.md).

## <a name="connection-type"></a>Tipo de ligação

Selecione o tipo de conexão VPN na lista de fornecedores a seguir:

- **Check Point Capsule VPN**
- **AnyConnect herdado Cisco**: Aplicável ao [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) app versão 4.0.5 x e versões anteriores.
- **Cisco AnyConnect**: Aplicável ao [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) app versão 4.0.7 x e posterior.
- **SonicWall Mobile Connect**
- **F5 acesso herdado**: Aplicável a F5 Access app versão 2,1 e anteriores.
- **Acesso ao F5**: Aplicável a F5 Access app versão 3,0 e posterior.
- **Palo Alto Networks GlobalProtect (Herdado)** : Aplicável ao Palo Alto Networks GlobalProtect app versão 4,1 e versões anteriores.
- **Palo Alto Networks GlobalProtect**: Aplicável ao Palo Alto Networks GlobalProtect app versão 5,0 e posterior.
- **Pulse Secure**
- **Cisco (IPSec)**
- **VPN do Citrix**
- **Citrix SSO**
- **Zscaler**: Para usar o acesso condicional ou permitir que os usuários ignorem a tela de entrada do Zscaler, você deve integrar o ZPA (Zscaler Private Access) à sua conta do Azure AD. Para obter passos detalhados, veja a [documentação do Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **IKEv2**: [Configurações IKEv2](#ikev2-settings) (neste artigo) descreve as propriedades.
- **VPN Personalizada**

> [!NOTE]
> A Cisco, Citrix, F5 e Palo Alto anunciaram que os seus clientes legados não funcionam no iOS 12. Deverá migrar para as novas aplicações logo que possível. Para obter mais informações, veja o [Blogue da Equipa de Suporte do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Definições de VPN Base

As definições apresentadas na seguinte lista são determinadas pelo tipo de ligação VPN que escolher.  

- **Nome da conexão**: Os utilizadores finais verão este nome quando procurarem uma lista de ligações VPN disponíveis no dispositivo.
- **Nome de domínio personalizado** (Somente Zscaler): Preencha o campo de entrada do aplicativo Zscaler com o domínio ao qual os usuários pertencem. Por exemplo, se um nome de utilizador for `Joe@contoso.net`, o domínio `contoso.net` será apresentado estaticamente no campo ao abrir a aplicação. Se não introduzir um nome de domínio, será utilizada a parte do domínio do UPN no Azure Active Directory (AD).
- **Endereço IP ou FQDN**: O endereço IP ou FQDN (nome de domínio totalmente qualificado) do servidor VPN ao qual os dispositivos se conectam. Por exemplo, introduza: `192.168.1.1` ou `vpn.contoso.com`.
- **Nome da nuvem da organização** (Somente Zscaler): Insira o nome da nuvem em que sua organização está provisionada. O URL que utiliza para iniciar sessão no Zscaler contém o nome.  
- **Método de autenticação**: Escolha como os dispositivos são autenticados no servidor VPN. 
  - **Certificados**: Em **certificado de autenticação**, selecione um perfil de certificado SCEP ou PKCS existente para autenticar a conexão. O tópico [Configurar certificados](../protect/certificates-configure.md) fornece algumas orientações sobre perfis de certificado.
  - **Nome de usuário e senha**: Os usuários finais devem inserir um nome de usuário e senha para entrar no servidor VPN.  

    > [!NOTE]
    > Se o nome de utilizador e a palavra-passe forem utilizados como o método de autenticação do Cisco IPsec VPN, os primeiros têm de enviar o parâmetro SharedSecret através de um perfil personalizado do Apple Configurator.

- **URLs excluídas** (Somente Zscaler): Quando conectado à VPN Zscaler, as URLs listadas podem ser acessadas fora da nuvem Zscaler. 

- **Túnel dividido**: **Habilitar** ou **desabilitar** para permitir que os dispositivos decidam qual conexão usar, dependendo do tráfego. Por exemplo, um utilizador num hotel utiliza a ligação VPN para aceder aos ficheiros de trabalho, mas utiliza a rede padrão do hotel para a navegação normal na Internet.

- **Identificador de VPN** (VPN personalizada, Zscaler e Citrix): Um identificador para o aplicativo VPN que você está usando e é fornecido pelo seu provedor de VPN.
  - **Insira os pares de chave/valor para os atributos de VPN personalizados da sua organização**: Adicione ou importe **chaves** e **valores** que personalizam sua conexão VPN. Lembre-se de que estes valores são habitualmente disponibilizados pelo seu fornecedor de VPN.

- **Habilitar o NAC (controle de acesso à rede)** (Citrix SSO, acesso F5): Quando você escolhe **concordo**, a ID do dispositivo é incluída no perfil de VPN. Essa ID pode ser usada para autenticação na VPN para permitir ou impedir o acesso à rede.

  **Ao usar o acesso F5**, certifique-se de:

  - Confirme que você está usando F5 BIG-IP 13.1.1.5. Não há suporte para BIG-IP 14.
  - Integre BIG-IP ao Intune para NAC. Consulte a [visão geral: Configurando o APM para verificações de postura de](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) dispositivo com o guia F5 dos sistemas de gerenciamento de pontos
  - Habilite o NAC no perfil de VPN.

  **Ao usar o SSO da Citrix com o gateway**, certifique-se de:

  - Confirme que você está usando o Citrix gateway 12.0.59 ou superior.
  - Confirme se os usuários têm o Citrix SSO 1.1.6 ou posterior instalado em seus dispositivos.
  - Integrar o gateway do Citrix ao Intune para NAC. Consulte o guia de implantação da Citrix para [integração do Microsoft Intune/Enterprise Mobility Suite com Netscaler (LDAP + OTP)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) .
  - Habilite o NAC no perfil de VPN.

  **Detalhes importantes**:  

  - Quando o NAC está habilitado, a VPN é desconectada a cada 24 horas. A VPN pode ser imediatamente reconectada.
  - A ID do dispositivo faz parte do perfil, mas não é mostrada no Intune. Este ID não é armazenado nem partilhado pela Microsoft.

  Quando a ID do dispositivo é suportada por parceiros de VPN, o cliente VPN, como o Citrix SSO, pode obter a ID. Em seguida, ele pode consultar o Intune para confirmar se o dispositivo está registrado e se o perfil VPN está em conformidade ou não em conformidade.

  - Para remover esta definição, volte a criar o perfil e não selecione a opção **Concordo**. Em seguida, atribua novamente o perfil.

## <a name="ikev2-settings"></a>Configurações IKEv2

Essas configurações se aplicam quando você escolhe o **tipo** > de conexão**IKEv2**.

- **Identificador remoto**: Insira o endereço IP de rede, o FQDN, o userfqdn ou o ASN1DN do servidor IKEv2. Por exemplo, introduza: `10.0.0.3` ou `vpn.contoso.com`. Normalmente, você insere o mesmo valor que o [**nome da conexão**](#base-vpn-settings) (neste artigo). Mas, isso depende de suas configurações de servidor IKEv2.

- **Tipo de autenticação de cliente**: Escolha como o cliente VPN é autenticado na VPN. As opções são:
  - **Autenticação do usuário** (padrão): As credenciais do usuário são autenticadas para a VPN.
  - **Autenticação do computador**: As credenciais do dispositivo são autenticadas para a VPN.

- **Método de autenticação**: Escolha o tipo de credenciais de cliente para enviar ao servidor. As opções são:
  - **Certificados**: Usa um perfil de certificado existente para autenticar para a VPN. Verifique se esse perfil de certificado já está atribuído ao usuário ou dispositivo. Caso contrário, a conexão VPN falhará.
    - **Tipo de certificado**: Selecione o tipo de criptografia usado pelo certificado. Verifique se o servidor VPN está configurado para aceitar esse tipo de certificado. As opções são:
      - **RSA** os
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Nome de usuário e senha** (Somente autenticação do usuário): Quando os usuários se conectam à VPN, eles são solicitados a fornecer seu nome de usuário e senha.
  - **Segredo compartilhado** (Somente autenticação do computador): Permite que você insira um segredo compartilhado para enviar ao servidor VPN.
    - **Segredo compartilhado**: Insira o segredo compartilhado, também conhecido como chave pré-compartilhada (PSK). Verifique se o valor corresponde ao segredo compartilhado configurado no servidor VPN.

- **Nome comum do emissor do certificado do servidor**: Permite que o servidor VPN se autentique no cliente VPN. Insira o nome comum do emissor do certificado (CN) do certificado do servidor VPN que é enviado para o cliente VPN no dispositivo. Verifique se o valor CN corresponde à configuração no servidor VPN. Caso contrário, a conexão VPN falhará.
- **Nome comum do certificado do servidor**: Insira o CN para o certificado em si. Se for deixado em branco, o valor do identificador remoto será usado.

- **Taxa de detecção de pares inativos**: Escolha a frequência com que o cliente VPN verifica se o túnel VPN está ativo. As opções são:
  - **Não configurado**: Usa o padrão do sistema iOS, que pode ser o mesmo que escolher **médio**.
  - **Nenhum**: Desabilita a detecção de pares inativos.
  - **Baixo**: Envia uma mensagem de KeepAlive a cada 30 minutos.
  - **Média** (padrão): Envia uma mensagem de KeepAlive a cada 10 minutos.
  - **Alto**: Envia uma mensagem KeepAlive a cada 60 segundos.

- **Intervalo de versão do TLS mínimo**: Insira a versão mínima do TLS a ser usada. Insira `1.0`, `1.1`ou .`1.2` Se for deixado em branco, o valor `1.0` padrão de será usado.
- **Máximo do intervalo de versão do TLS**: Insira a versão máxima do TLS a ser usada. Insira `1.0`, `1.1`ou .`1.2` Se for deixado em branco, o valor `1.2` padrão de será usado.
- **Sigilo perfeita no encaminhamento**: Selecione **habilitar** para ativar o PFS (sigilo de encaminhamento perfeito). O PFS é um recurso de segurança IP que reduz o impacto se uma chave de sessão for comprometida. **Desabilitar** (padrão) não usa PFS.
- **Verificação de revogação de certificado**: Selecione **habilitar** para garantir que os certificados não sejam revogados antes de permitir que a conexão VPN seja realizada com sucesso. Essa verificação é de melhor esforço. Se o servidor VPN expirar antes de determinar se o certificado foi revogado, o acesso será concedido. **Desabilitar** (padrão) não verifica se há certificados revogados.

- **Configurar parâmetros de associação de segurança**: **Não configurado** (padrão) usa o padrão do sistema iOS. Selecione **habilitar** para inserir os parâmetros usados ao criar associações de segurança com o servidor VPN:
  - **Algoritmo de criptografia**: Selecione o algoritmo desejado:
    - DES
    - 3DES
    - AES-128
    - AES-256 (padrão)
    - AES-128-GCM
    - AES-256-GCM
  - **Algoritmo de integridade**:  Selecione o algoritmo desejado:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (padrão)
    - SHA2-384
    - SHA2-512
  - **Grupo Diffie-Hellman**: Selecione o grupo desejado. O padrão é `2`grupo.
  - **Tempo de vida** (minutos): Escolha quanto tempo a associação de segurança permanecerá ativa até que as chaves sejam giradas. Insira um valor inteiro entre `10` e `1440` (1440 minutos é 24 horas). A predefinição é `1440`.

- **Configurar um conjunto separado de parâmetros para associações de segurança filho**: o Ios permite que você configure parâmetros separados para a conexão Ike e quaisquer conexões filho. 

  **Não configurado** (padrão) usa os valores inseridos na configuração anterior **definir parâmetros de associação de segurança** . Selecione **habilitar** para inserir os parâmetros usados ao criar associações de segurança *filho* com o servidor VPN:
  - **Algoritmo de criptografia**: Selecione o algoritmo desejado:
    - DES
    - 3DES
    - AES-128
    - AES-256 (padrão)
    - AES-128-GCM
    - AES-256-GCM
  - **Algoritmo de integridade**:  Selecione o algoritmo desejado:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (padrão)
    - SHA2-384
    - SHA2-512
  - **Grupo Diffie-Hellman**: Selecione o grupo desejado. O padrão é `2`grupo.
  - **Tempo de vida** (minutos): Escolha quanto tempo a associação de segurança permanecerá ativa até que as chaves sejam giradas. Insira um valor inteiro entre `10` e `1440` (1440 minutos é 24 horas). A predefinição é `1440`.

## <a name="automatic-vpn-settings"></a>Definições Automáticas de VPN

- **VPN por aplicativo**: Habilita a VPN por aplicativo. Permite que a ligação VPN seja acionada automaticamente quando determinadas aplicações forem abertas. Também associa as aplicações com este perfil VPN. Para obter mais informações, veja as [instruções para configurar a VPN por aplicação para iOS](vpn-setting-configure-per-app.md).
  - **Tipo de provedor**: Disponível somente para VPN de pulso seguro e personalizado.
  - Ao utilizar perfis **VPN por aplicação** iOS com o Pulse Secure ou uma VPN Personalizada, selecione o túnel de camada de aplicação (proxy-de-aplicação) ou o túnel de nível do pacote (pacote-túnel). Defina o valor **ProviderType** para **proxy-da-aplicação**, para o túnel de camada de aplicação ou para **pacote-túnel**, para o túnel de camada de pacote. Se não tiver a certeza sobre o valor a utilizar, consulte a documentação do seu fornecedor de VPN.
  - **URLs do safari que dispararão esta VPN**: Adicione uma ou mais URLs de site. Quando estes URLs são visitados através do browser Safari no dispositivo, a ligação VPN é estabelecida automaticamente.

- **VPN sob demanda**: Configure regras condicionais que controlam quando a conexão VPN é iniciada. Por exemplo, crie uma condição na qual a ligação VPN só é utilizada quando um dispositivo não estiver ligado a uma rede Wi-Fi da sua empresa. Ou crie uma condição. Por exemplo, se um dispositivo não puder acessar um domínio de pesquisa DNS inserido, a conexão VPN não será iniciada.

  - **Domínios de pesquisa de DNS ou SSIDs**: Selecione se essa condição usa **SSIDs**de rede sem fio ou **domínios de pesquisa DNS**. Selecione **Adicionar** para configurar um ou mais SSIDs ou domínios de pesquisa.
  - **Investigação da cadeia de caracteres de URL**: Opcional. Introduza um URL para a regra utilizar como um teste. Se o dispositivo com esse perfil acessar essa URL sem redirecionamento, a conexão VPN será iniciada. Além disso, o dispositivo será ligado ao URL de destino. O utilizador não vê o site de pesquisa de cadeia de URL. Um exemplo de uma pesquisa de cadeia de URL é o endereço de um servidor Web de auditoria que verifica a conformidade do dispositivo antes de ligar a VPN. Outra possibilidade é a de o URL testar a capacidade de a VPN estabelecer ligação a um site, antes de ligar o dispositivo ao URL de destino através da VPN.
  - **Ação de domínio**: Escolha um dos seguintes itens:
    - Ligar se necessário
    - Nunca ligar
  - **Ação**: Escolha um dos seguintes itens:
    - Ligar
    - Avaliar a ligação
    - Ignorar
    - Desligar

## <a name="proxy-settings"></a>Definições de proxy

Se estiver a utilizar um proxy, configure as definições seguintes. As definições de proxy não estão disponíveis para ligações VPN do Zscaler.  

- **Script de configuração automática**: Use um arquivo para configurar o servidor proxy. Introduza o **URL do servidor proxy** (por exemplo, `http://proxy.contoso.com`) que inclui o ficheiro de configuração.
- **Endereço**: Insira o endereço IP do nome de host totalmente qualificado do servidor proxy.
- **Número da porta**: Insira o número da porta associada ao servidor proxy.

## <a name="next-steps"></a>Passos seguintes

O perfil está criado, mas ainda não está ativo. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitorize o estado](device-profile-monitor.md).

Defina as configurações de VPN em dispositivos [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)e [Windows 10](vpn-settings-windows-10.md) .
