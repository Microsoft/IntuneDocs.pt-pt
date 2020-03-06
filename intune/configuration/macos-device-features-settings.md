---
title: as definições de funcionalidades do dispositivo macOS no Microsoft Intune - Azure / Microsoft Docs
description: Consulte as definições para configurar dispositivos macOS para AirPrint e personalize a janela de Login para mostrar ou ocultar botões de energia no Microsoft Intune. Consulte os passos para obter as definições de endereço IP, caminho e porta de um servidor AirPrint na sua rede. Utilize estas definições num perfil de configuração do dispositivo para configurar as funcionalidades do dispositivo macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369841"
---
# <a name="macos-device-feature-settings-in-intune"></a>funcionalidade do dispositivo macOS em Intune

Intune inclui algumas configurações incorporadas para personalizar funcionalidades nos seus dispositivos macOS. Por exemplo, os administradores podem adicionar impressoras AirPrint, escolher como os utilizadores entram, configurar os controlos de energia, usar a autenticação de entrada única e muito mais.

Utilize estas funcionalidades para controlar dispositivos macOS como parte da sua solução de gestão de dispositivos móveis (MDM).

Este artigo lista estas definições e descreve o que cada definição faz. Também lista os passos para obter o endereço IP, caminho e impressoras porta de AirPrint usando a aplicação Terminal (emulador). Para obter mais informações sobre as funcionalidades do dispositivo, vá a adicionar definições de funcionalidades de [dispositivos iOS/iPadOS ou macOS](device-features-configure.md).

## <a name="before-you-begin"></a>Antes de começar

Criar um perfil de configuração do [dispositivo macOS](device-features-configure.md).

> [!NOTE]
> Estas configurações aplicam-se a diferentes tipos de matrículas, com algumas definições aplicáveis a todas as opções de inscrição. Para obter mais informações sobre os diferentes tipos de matrículas, consulte a [inscrição do macOS.](../enrollment/macos-enroll.md)

## <a name="airprint"></a>Impressão Aérea

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos 

- **Endereço IP**: Introduza o endereço IPv4 ou IPv6 da impressora. Se utilizar os nomes do anfitrião para identificar impressoras, pode obter o endereço IP através do pingping da impressora na aplicação Terminal. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Caminho**: Entre no caminho da impressora. O caminho é tipicamente `ipp/print` para impressoras na sua rede. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Porta** (iOS 11.0+, iPadOS 13.0+): Introduza a porta de escuta do destino AirPrint. Se deixar esta propriedade em branco, o AirPrint utiliza a porta predefinida.
- **TLS** (iOS 11.0+, iPadOS 13.0+): Select **Enable** para assegurar ligações AirPrint com Segurança da Camada de Transporte (TLS).

- **Adicionar** O servidor da AirPrint. Pode adicionar muitos servidores AirPrint.

Também pode **importar** um ficheiro separado de vírvias (.csv) que inclui uma lista de impressoras AirPrint. Além disso, depois de adicionar impressoras AirPrint em Intune, pode **exportar** esta lista.

### <a name="get-the-ip-address-and-path"></a>Obtenha o endereço IP e o caminho

Para adicionar servidores AirPrinter, precisa do endereço IP da impressora, do caminho dos recursos e da porta. Os seguintes passos mostram-lhe como obter esta informação.

1. Num Mac que esteja ligado à mesma rede local (subnet) que as impressoras AirPrint, **terminal** aberto (de **/Aplicações/Utilitários).**
2. Na aplicação Terminal, escreva `ippfind`, e selecione entrar.

    Repare na informação da impressora. Por exemplo, pode devolver algo semelhante ao `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é a via de recursos.

3. No Terminal, digite `ping myprinter.local`, e selecione entrar.

   Note o endereço IP. Por exemplo, pode devolver algo semelhante ao `PING myprinter.local (10.50.25.21)`.

4. Utilize os valores do endereço IP e do caminho dos recursos. Neste exemplo, o endereço IP é `10.50.25.21`, e o caminho dos recursos é `/ipp/port1`.

## <a name="login-items"></a>Itens de login

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Ficheiros, pastas e aplicações personalizadas**: **Adicione** o caminho de um ficheiro, pasta, aplicação personalizada ou aplicação do sistema que pretende abrir quando um utilizador faz o sinal de si no dispositivo. Aplicações do sistema, ou aplicações construídas ou personalizadas para a sua organização estão tipicamente na pasta `Applications`, com um caminho semelhante ao `/Applications/AppName.app`. 

  Pode adicionar muitos ficheiros, pastas e aplicações. Por exemplo, introduza:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ao adicionar qualquer aplicação, pasta ou ficheiro, certifique-se de que introduza o caminho correto. Nem todos os itens estão na pasta `Applications`. Se um utilizador move um item de um local para outro, então o caminho muda. Este item movido não será aberto quando o utilizador entrar.

## <a name="login-window"></a>Janela de login

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Definições aplicam-se a: Inscrição do dispositivo e inscrição automática de dispositivos

#### <a name="window-layout"></a>Layout da janela

- **Mostre informações adicionais na barra de menus**: Quando a área de tempo na barra de menus for selecionada, **permita** mostrar o nome do anfitrião e a versão macOS. **Não configurado** (predefinido) não mostra esta informação na barra de menus.
- **Banner**: Introduza uma mensagem que está mostrada no sinal no ecrã do dispositivo. Por exemplo, insira as informações da sua organização, uma mensagem de boas-vindas, informação perdida e encontrada, e assim por diante.
- Escolha o **formato de login**: Escolha como os utilizadores iniciam sessão no dispositivo. As opções são:
  - **Solicitação para o nome de utilizador e palavra-passe** (predefinição): Requer que os utilizadores introduzam um nome de utilizador e uma palavra-passe.
  - **Liste todos os utilizadores, indique a palavra-passe**: Requer que os utilizadores selecionem o seu nome de utilizador a partir de uma lista de utilizadores e, em seguida, introduzam a sua palavra-passe. Também configurar:

    - **Utilizadores locais**: **O Hide** não mostra as contas de utilizador locais na lista de utilizadores, o que pode incluir as contas padrão e de administração. Apenas são apresentadas as contas de utilizador da rede e do sistema. **Não configurado** (predefinido) mostra as contas de utilizador locais na lista de utilizadores.
    - **Contas móveis:** **O Hide** não mostra contas móveis na lista de utilizadores. **Não configurado** (predefinido) mostra as contas móveis na lista de utilizadores. Algumas contas móveis podem mostrar como utilizadores da rede.
    - **Utilizadores da rede**: Selecione **Mostrar** para listar os utilizadores da rede na lista de utilizadores. **Não configurado** (predefinido) não mostra as contas de utilizador da rede na lista de utilizadores.
    - **Utilizadores de administrador:** **O Hide** não mostra as contas de utilizador do administrador na lista de utilizadores. **Não configurado** (predefinido) mostra as contas de utilizador do administrador na lista de utilizadores.
    - **Outros utilizadores**: Selecione **Mostrar** para **listar Outros...** utilizadores na lista de utilizadores. **Não configurado** (predefinido) não mostra as outras contas de utilizador na lista de utilizadores.

#### <a name="login-screen-power-settings"></a>Definições de potência do ecrã de login

- **Botão desligar**: **Ocultar** não mostra o botão de paragem no sinal no ecrã. **Não configurado** (predefinido) mostra o botão de paragem.
- **Botão de reiniciar**: **Ocultar** não mostra o botão de reiniciar o sinal no ecrã. **Não configurado** (predefinido) mostra o botão de reinício.
- **Botão de sono**: **O hide** não mostra o botão de sono no sinal no ecrã. **Não configurado** (predefinido) mostra o botão de sono.

#### <a name="other"></a>Outros

- **Desative o login do utilizador a partir da Consola:** **Desative** a linha de comando macOS utilizada para iniciar sessão. Para utilizadores típicos, **desative** esta definição. **Não configurado** (predefinido) permite que os utilizadores avançados assinem utilizando a linha de comando macOS. Para entrar no modo consola, os utilizadores introduzem `>console` no campo Username e devem autenticar na janela da consola.

#### <a name="apple-menu"></a>Apple Menu

Depois de os utilizadores iniciarem sessão nos dispositivos, as seguintes definições têm impacto no que podem fazer.

- **Desligar**: **Desativar** impede os utilizadores de selecionar a opção **Desligar** após a instinação do utilizador. **Não configurado** (predefinido) permite que os utilizadores selecionem o item do menu **'Desligar'** no dispositivo.
- **Desativar O arranque**: **Desativar** impede os utilizadores de selecionar a opção **Reiniciar** após a intenção do utilizador. **Não configurado** (predefinido) permite que os utilizadores selecionem o item do menu **Restart** no dispositivo.
- **Desativar o desativado**: **Desativar** os utilizadores impede que os utilizadores selecionem a opção Desligar a **desativação** após a insactivação do utilizador. **Não configurado** (predefinido) permite que os utilizadores selecionem o item do menu **Desligar** no dispositivo.
- **Desativar o Log out** (macOS 10.13 e mais tarde): **Desativar** os utilizadores impede que os utilizadores selecionem a opção **Iniciar sessão** após a hora do utilizador. **Não configurado** (predefinido) permite que os utilizadores selecionem o item do menu **'Iniciar sessão'** no dispositivo.
- **Desativar** o ecrã de bloqueio (macOS 10.13 e mais tarde): **Desativar** os utilizadores impede que os utilizadores selecionem a opção de **ecrã de bloqueio** após a instinação do utilizador. **Não configurado** (predefinido) permite que os utilizadores selecionem o item do menu **do ecrã lock** no dispositivo.

## <a name="single-sign-on-app-extension"></a>Extensão única da aplicação de inscrição

Esta funcionalidade aplica-se a:

- macOS 10.15 e mais recente

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição 

- **Tipo de extensão da aplicação SSO**: Escolha o tipo de extensão da aplicação SSO credencial. As opções são:

  - **Não configurado**: As extensões de aplicações não são utilizadas. Para desativar uma extensão da aplicação, altere o tipo de extensão da aplicação SSO para **Não configurado**.
  - **Redirecionamento**: Utilize uma extensão de aplicação de redirecionamento genérica e personalizável para executar SSO com fluxos de autenticação modernos. Certifique-se de que conhece a extensão e o ID da equipa para a extensão da aplicação da sua organização.
  - **Credencial**: Utilize uma extensão de aplicação credencial genérica e personalizável para executar SSO com fluxos de autenticação de desafio e resposta. Certifique-se de que conhece o ID de extensão e o ID da equipa para a extensão da aplicação SSO da sua organização.  
  - **Kerberos**: Use a extensão Kerberos incorporada da Apple, que está incluída no macOS Catalina 10.15 e mais recente. Esta opção é uma versão específica da Extensão da aplicação **Credencial** da Kerberos.

  > [!TIP]
  > Com os tipos **Redirecionamento** e **Credenciais,** adicione os seus próprios valores de configuração para passar pela extensão. Se estiver a utilizar o **Credential,** considere utilizar as configurações de configuração incorporadas fornecidas pela Apple no tipo **Kerberos.**

- **ID de extensão** (Redirecionamento e Credencial): Introduza o identificador de pacote que identifica a extensão da sua aplicação SSO, como `com.apple.ssoexample`.
- **ID da equipa** (Redirecionamento e Credencial): Introduza o identificador de equipa da extensão da sua aplicação SSO. Um identificador de equipa é uma cadeia alfanumérica de 10 caracteres (números e letras) gerada pela Apple, como `ABCDE12345`. 

  [Localizar o seu Team ID](https://help.apple.com/developer-account/#/dev55c3c710c) (abre o site da Apple) tem mais informações.

- **Reino** (Credencial e Kerberos): Introduza o nome do seu reino de autenticação. O nome do reino deve ser capitalizado, como `CONTOSO.COM`. Tipicamente, o seu nome de reino é o mesmo que o seu nome de domínio DNS, mas em todas as maiúsculas.

- **Domínios** (Credential e Kerberos): Introduza o domínio ou nomes de anfitriões dos sites que podem autenticar através do SSO. Por exemplo, se o seu website for `mysite.contoso.com`, então `mysite` é o nome do anfitrião, e `contoso.com` é o nome de domínio. Quando os utilizadores se ligam a qualquer um destes sites, a extensão da aplicação trata do desafio de autenticação. Esta autenticação permite que os utilizadores utilizem o Face ID, touch ID ou Apple pincode/código de acesso para iniciar sessão.

  - Todos os domínios da sua única extensão de aplicação de início de sessão Os perfis Intune devem ser únicos. Não é possível repetir um domínio em qualquer perfil de extensão de aplicações de início de sessão, mesmo que esteja a utilizar diferentes tipos de extensões de aplicações SSO.
  - Estes domínios não são sensíveis a casos.

- **URLs** (apenas redirecionamento): Introduza os prefixos URL dos seus fornecedores de identidade em nome de quem a extensão da aplicação de redirecionamento executa SSO. Quando um utilizador é redirecionado para estes URLs, a extensão da aplicação SSO intervirá e solicitará sSO.

  - Todos os URLs nos seus perfis de extensão de aplicações intune devem ser únicos. Não é possível repetir um domínio em qualquer perfil de extensão de aplicações SSO, mesmo que esteja a utilizar diferentes tipos de extensões de aplicações SSO.
  - Os URLs devem começar com http:// ou https://.

- **Configuração adicional** (Redirecionamento e Credencial): Introduza dados adicionais específicos de extensão para passar para a extensão da aplicação SSO:
  - **Chave**: Introduza o nome do item que pretende adicionar, como `user name`.
  - **Tipo**: Introduza o tipo de dados. As opções são:

    - Cadeia
    - Boolean: No valor de **configuração,** introduza `True` ou `False`.
    - Integer: No valor de **configuração,** introduza um número.
    
  - **Valor**: Introduza os dados.
  
  - **Adicione**: Selecione para adicionar as suas chaves de configuração.

- **Utilização** em cadeia de chaves (apenas Kerberos): Escolha **o Bloco** para evitar que as palavras-passe sejam guardadas e armazenadas no porta-chaves. **Não configurado** (predefinido) permite que as palavras-passe sejam guardadas e armazenadas no porta-chaves.  
- **Face ID, Touch ID ou código de acesso** (apenas Kerberos): **Exigir** que os utilizadores introduzam o seu Id Facial, Touch ID ou Apple passcode para iniciar sessão nos domínios que adicionou. **Não configurado** (predefinido) não requer que os utilizadores utilizem biometria ou código de acesso para iniciar sessão.
- **Reino padrão** (apenas Kerberos): Escolha **ativar** para definir o valor real **que** introduziu como o reino padrão. **Não configurado** (predefinido) não define um reino predefinido.

  > [!TIP]
  > - **Ative** esta definição se estiver a configurar várias extensões de aplicações Kerberos SSO na sua organização.
  > - **Ative** esta definição se estiver a utilizar vários reinos. Define o valor do **Reino** que introduziu como o reino padrão.
  > - Se tiver apenas um reino, deixe-o **não configurado** (predefinido).

- **Autodescubra** (apenas Kerberos): Quando definida para **bloquear,** a extensão Kerberos não utiliza automaticamente LDAP e DNS para determinar o seu nome de site ative diretório. **Não configurado** (predefinido) permite que a extensão encontre automaticamente o nome do site do Diretório Ativo.
- **Alterações de palavra-passe** (apenas Kerberos): **O bloco** impede que os utilizadores mudem as palavras-passe que utilizam para iniciar sessão nos domínios em que inseriu. **Não configurado** (predefinido) permite alterações de palavra-passe.  
- **Sincronização de passwords** (apenas Kerberos): Escolha **ativar** para sincronizar as palavras-passe locais dos seus utilizadores para o Azure AD. **Não configurado** (padrão) desativa a sincronização de palavras-passe para o Azure AD. Utilize esta definição como alternativa ou cópia de segurança para o SSO. Esta definição não funciona se os utilizadores forem inscritos numa conta móvel da Apple.
- Complexidade da **palavra-passe do Diretório Ativo do Windows Server** (apenas Kerberos): Escolha **exigir** que as palavras-passe dos utilizadores cumpram os requisitos de complexidade da palavra-passe do Ative Directory. Ver [Palavra-passe deve satisfazer os requisitos](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) de complexidade para mais informações. **Não configurado** (predefinido) não requer que os utilizadores cumpram o requisito de palavra-passe do Diretório Ativo.
- Comprimento mínimo da **palavra-passe** (apenas Kerberos): Introduza o número mínimo de caracteres que podem compor a palavra-passe de um utilizador. **Não configurado** (predefinido) não impõe um comprimento mínimo de senha nos utilizadores.
- Limite de **reutilização de palavra-passe** (apenas Kerberos): Introduza o número de novas senhas, de 1 a 24, que devem ser utilizadas até que uma palavra-passe anterior possa ser reutilizada no domínio. **Não configurado** (predefinido) não impõe um limite de reutilização da palavra-passe.
- Idade mínima da **palavra-passe** (apenas Kerberos): Introduza o número de dias em que uma palavra-passe deve ser utilizada no domínio antes que um utilizador possa alterá-la. **Não configurado** (predefinido) não impõe uma idade mínima de senhas antes de poderem ser alteradas.
- Notificação de expiração de **palavra-passe** (apenas Kerberos): Insira o número de dias antes de expirar uma palavra-passe para que os utilizadores sejam notificados de que a sua palavra-passe expirará. **Não configurado** (predefinido) utiliza `15` dias.
- **Expiração da palavra-passe** (apenas Kerberos): Introduza o número de dias antes de a palavra-passe do dispositivo ser alterada. **Não configurado** (predefinido) significa que as palavras-passe do utilizador nunca expiram.
- **URL** de alteração de password (apenas Kerberos): Introduza o URL que é lançado quando o utilizador inicia uma alteração de senha kerberos.
- **Nome principal** (apenas Kerberos): Introduza o nome de utilizador do diretor kerberos. Não precisas de incluir o nome do reino. Por exemplo, em `user@contoso.com`, `user` é o nome principal, e `contoso.com` é o nome do reino.

  > [!TIP]
  > - Também pode utilizar variáveis no nome principal, entrando em suportes encaracolados `{{ }}`. Por exemplo, para mostrar o nome de utilizador, insira `Username: {{username}}`. 
  > - No entanto, tenha cuidado com a substituição variável porque as variáveis não são validadas na UI e são sensíveis ao caso. Certifique-se de introduzir a informação correta.
  
- Código de **site de Diretório Ativo** (apenas Kerberos): Introduza o nome do site Ative Directory que a extensão Kerberos deve utilizar. Pode não precisar de alterar este valor, uma vez que a extensão Kerberos pode automaticamente encontrar o código do site do Ative Directory.
- **Nome cache** (apenas Kerberos): Introduza o nome genérico de serviços de segurança (GSS) da cache Kerberos. Provavelmente não precisa definir este valor.  
- **Mensagem de prescrição de palavra-passe** (apenas Kerberos): Introduza uma versão de texto dos requisitos de palavra-passe da sua organização que é mostrada aos utilizadores. A mensagem é mostrada se não necessitar dos requisitos de complexidade da palavra-passe do Ative Directory ou se não introduzir um comprimento mínimo de senha.  
- **IDs** de pacote de aplicativos (apenas Kerberos): **Adicione** os identificadores de pacote de aplicativos que devem usar um único sinal nos seus dispositivos. Estas aplicações têm acesso ao Bilhete de Concessão de Bilhetes Kerberos, ao bilhete de autenticação e autenticam os utilizadores aos serviços a que estão autorizados a aceder.
- **Mapeamento** do domínio (apenas Kerberos): **Adicione** os sufixos dNS de domínio que devem mapear para o seu reino. Use este cenário quando os nomes DNS dos anfitriões não corresponderem ao nome do reino. Provavelmente não precisa de criar este mapeamento personalizado domínio-realm.
- **Certificado PKINIT** (apenas Kerberos): **Selecione** o certificado de criptografia de chave pública para autenticação inicial (PKINIT) que pode ser usado para autenticação Kerberos. Pode escolher entre os certificados [PKCS](../protect/certficates-pfx-configure.md) ou [SCEP](../protect/certificates-scep-configure.md) que adicionou no Intune. Para obter mais informações sobre certificados, consulte [Utilize certificados para autenticação no Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Domínios associados

Em Intune, pode:

- Adicione muitas associações app-to-domain.
- Associe muitos domínios com a mesma app.

Esta funcionalidade aplica-se a:

- macOS 10.15 e mais recente

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- Id da **aplicação**: Introduza o identificador de aplicações da app para se associar a um website. O identificador de aplicações inclui o ID da equipa e um pacote de identificação: `TeamID.BundleID`.

  O ID da equipa é uma cadeia alfanumérica de 10 caracteres (letras e números) gerada pela Apple para os desenvolvedores de aplicações, como `ABCDE12345`. [Localize o seu](https://help.apple.com/developer-account/#/dev55c3c710c) de ID da equipa (abre o site da Apple) tem mais informações.

  O id do pacote identifica exclusivamente a app, e tipicamente é formatado em notação de nome de domínio invertido. Por exemplo, o id de pacote do Finder é `com.apple.finder`. Para encontrar o ID do pacote, utilize o AppleScript no Terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domínio**: Insira o domínio do site para se associar a uma aplicação. O domínio inclui um tipo de serviço e um nome de anfitrião totalmente qualificado, como `webcredentials: www.contoso.com`.

  Pode combinar todos os subdomínios de um domínio associado introduzindo `*.` (um wildcard asterisco e um período) antes do início do domínio. O período é necessário. Os domínios exatos têm uma prioridade maior do que os domínios wildcard. Assim, os padrões dos domínios dos pais são combinados *se* uma correspondência não for encontrada no subdomínio totalmente qualificado.

  O tipo de serviço pode ser:

  - **authsrv**: Extensão única da aplicação de sinalização
  - **applink**: Ligação universal
  - **webcredenciais**: Autofill password

- **Adicione:** Selecione para adicionar as suas aplicações e domínios associados.

> [!TIP]
> Para resolver problemas, no seu dispositivo macOS, abra **as Preferências do Sistema** > **Perfis**. Confirme que o perfil que criou está na lista de perfis do dispositivo. Se estiver listado, certifique-se de que a Configuração de **Domínios Associados** está no perfil, e inclui o ID e domínios corretos da aplicação.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode configurar as funcionalidades do dispositivo no [iOS/iPadOS](ios-device-features-settings.md).
