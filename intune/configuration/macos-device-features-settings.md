---
title: configurações de recurso de dispositivo macOS no Microsoft Intune – Azure | Microsoft Docs
description: Consulte as configurações para configurar dispositivos macOS para o esprima e personalizar a janela de logon para mostrar ou ocultar botões de energia no Microsoft Intune. Consulte as etapas para obter o endereço IP, o caminho e as configurações de porta de um servidor de impressão em sua rede. Use essas configurações em um perfil de configuração de dispositivo para configurar recursos de dispositivo macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
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
ms.openlocfilehash: 48cca2c894067439943bdfff33b953463e513490
ms.sourcegitcommit: e9cf372711ff186ed468b01a9204631a139bd8e5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776918"
---
# <a name="macos-device-feature-settings-in-intune"></a>configurações de recurso de dispositivo macOS no Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune inclui algumas configurações internas para personalizar recursos em seus dispositivos macOS. Por exemplo, os administradores podem adicionar impressoras de impressão, escolher como os usuários entram, configurar os controles de energia, usar a autenticação de logon único e muito mais.

Use esses recursos para controlar dispositivos macOS como parte da sua solução de MDM (gerenciamento de dispositivo móvel).

Este artigo lista essas configurações e descreve o que cada configuração faz. Ele também lista as etapas para obter o endereço IP, o caminho e a porta de impressoras de impressão ao usar o aplicativo de terminal (emulador). Para obter mais informações sobre os recursos do dispositivo, vá para [Adicionar configurações de recurso do dispositivo IOS ou MacOS](device-features-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de dispositivo MacOS](device-features-configure.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro, com algumas configurações sendo aplicadas a todas as opções de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do MacOS](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado 

- **Endereço IP**: Insira o endereço IPv4 ou IPv6 da impressora. Se você usar nomes de host para identificar impressoras, poderá obter o endereço IP executando ping na impressora no aplicativo de terminal. [Obter o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Caminho**: Insira o caminho da impressora. Normalmente, o caminho é `ipp/print` para impressoras em sua rede. [Obter o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Porta** (Ios 11,0 e posterior): Insira a porta de escuta do destino de impressão. Se você deixar essa propriedade em branco, o impresso usará a porta padrão.
- **TLS** (Ios 11,0 e posterior): selecione **habilitar** para proteger conexões de esprint com segurança de camada de transporte (TLS).

- **Adicionar** O servidor de impressão. Você pode adicionar muitos servidores de impressão.

Você também pode **importar** um arquivo separado por vírgulas (. csv) que inclui uma lista de impressoras de impressão. Além disso, depois de adicionar impressoras de impressão no Intune, você pode **Exportar** essa lista.

### <a name="get-the-ip-address-and-path"></a>Obter o endereço IP e o caminho

Para adicionar servidores do servidor de impressão, você precisa do endereço IP da impressora, do caminho do recurso e da porta. As etapas a seguir mostram como obter essas informações.

1. Em um Mac que está conectado à mesma rede local (sub-rede) que as impressoras de impressão impressa, abra o **terminal** (de **/Applications/Utilities**).
2. No aplicativo de terminal, digite `ippfind` e selecione Enter.

    Anote as informações da impressora. Por exemplo, ele pode retornar algo semelhante a `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho do recurso.

3. No terminal, digite `ping myprinter.local` e selecione Enter.

   Anote o endereço IP. Por exemplo, ele pode retornar algo semelhante a `PING myprinter.local (10.50.25.21)`.

4. Use os valores de caminho de recurso e endereço IP. Neste exemplo, o endereço IP é `10.50.25.21` e o caminho do recurso é `/ipp/port1`.

## <a name="login-items"></a>Itens de logon

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Arquivos, pastas e aplicativos personalizados**: **adicione** o caminho de um arquivo, pasta, aplicativo personalizado ou aplicativo de sistema que você deseja abrir quando um usuário entrar no dispositivo. Aplicativos de sistema ou aplicativos criados ou personalizados para sua organização normalmente estão na pasta `Applications`, com um caminho semelhante a `/Applications/AppName.app`. 

  Você pode adicionar vários arquivos, pastas e aplicativos. Por exemplo, digite:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ao adicionar qualquer aplicativo, pasta ou arquivo, certifique-se de inserir o caminho correto. Nem todos os itens estão na pasta `Applications`. Se um usuário mover um item de um local para outro, o caminho será alterado. Este item movido não será aberto quando o usuário entrar.

## <a name="login-window"></a>Janela de logon

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>As configurações se aplicam a: registro de dispositivo e registro de dispositivo automatizado 

#### <a name="window-layout"></a>Layout da janela

- **Mostrar informações adicionais na barra de menus**: quando a área de tempo na barra de menus é selecionada, **permitir** mostra o nome do host e a versão do MacOS. **Não configurado** (padrão) não mostra essas informações na barra de menus.
- **Faixa**: Insira uma mensagem que é mostrada na tela de entrada no dispositivo. Por exemplo, insira as informações da sua organização, uma mensagem de boas-vindas, informações perdidas e encontradas e assim por diante.
- **Escolher o formato de logon**: escolha como os usuários entram no dispositivo. As opções são:
  - **Solicitar nome de usuário e senha** (padrão): requer que os usuários insiram um nome de usuário e uma senha.
  - **Listar todos os usuários, solicitar senha**: exige que os usuários selecionem seu nome de usuário em uma lista de usuários e, em seguida, insiram sua senha. Configure também:

    - **Usuários locais**: **ocultar** não mostra as contas de usuário local na lista de usuários, que podem incluir as contas padrão e de administrador. Somente as contas de usuário de rede e de sistema são mostradas. **Não configurado** (padrão) mostra as contas de usuário local na lista de usuários.
    - **Contas móveis**: **ocultar** não mostra contas móveis na lista de usuários. **Não configurado** (padrão) mostra as contas móveis na lista de usuários. Algumas contas móveis podem ser mostradas como usuários da rede.
    - **Usuários de rede**: selecione **Mostrar** para listar os usuários de rede na lista de usuários. **Não configurado** (padrão) não mostra as contas de usuário de rede na lista de usuários.
    - **Usuários administradores**: **ocultar** não mostra as contas de usuário administrador na lista de usuários. **Não configurado** (padrão) mostra as contas de usuário administrador na lista de usuários.
    - **Outros usuários**: selecione **Mostrar** para listar **outros...** usuários na lista de usuários. **Não configurado** (padrão) não mostra as outras contas de usuário na lista de usuários.

#### <a name="login-screen-power-settings"></a>Configurações de energia da tela de logon

- **Botão desligar**: **ocultar** não mostra o botão de desligamento na tela de entrada. **Não configurado** (padrão) mostra o botão de desligamento.
- **Botão reiniciar**: **ocultar** não mostra o botão reiniciar na tela de entrada. **Não configurado** (padrão) mostra o botão reiniciar.
- **Botão de suspensão**: **ocultar** não mostra o botão de suspensão na tela de entrada. **Não configurado** (padrão) mostra o botão de suspensão.

#### <a name="other"></a>Outros

- **Desabilitar logon de usuário do console**: **desabilitar** oculta a linha de comando MacOS usada para entrar. Para usuários típicos, **desabilite** essa configuração. **Não configurado** (padrão) permite que os usuários avançados entrem usando a linha de comando do MacOS. Para entrar no modo de console, os usuários inserem `>console` no campo username e devem ser autenticados na janela do console.

#### <a name="apple-menu"></a>Menu da Apple

Depois que os usuários entram nos dispositivos, as configurações a seguir afetam o que eles podem fazer.

- **Desabilitar desligar**: **desabilitar** impede que os usuários selecionem a opção de **desligamento** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu de **desligamento** no dispositivo.
- **Desabilitar reinicialização**: **desabilitar** impede que os usuários selecionem a opção de **reinicialização** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **reiniciar** no dispositivo.
- **Desabilitar desligar**: **desabilitar** impede que os usuários selecionem **a opção desligar após** o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **desligar** no dispositivo.
- **Desabilitar** logout (MacOS 10,13 e posterior): **desabilitar** impede que os usuários selecionem a opção **fazer logoff** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **fazer logoff** no dispositivo.
- **Desabilitar a tela de bloqueio** (MacOS 10,13 e posterior): **desabilitar** impede que os usuários selecionem a opção de **tela de bloqueio** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu da **tela de bloqueio** no dispositivo.

## <a name="single-sign-on-app-extension"></a>Extensão do aplicativo de logon único

Esta funcionalidade aplica-se a:

- macOS 10,15 e mais recente

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro 

- **Tipo de extensão do aplicativo SSO**: escolha o tipo de extensão do aplicativo de SSO de credencial. Ao salvar o perfil de extensão do aplicativo SSO, você não pode alterar o tipo de extensão do aplicativo SSO. As opções são:

  - **Não configurado**: as extensões de aplicativo não são usadas. Para desabilitar uma extensão de aplicativo SSO, alterne o tipo de extensão do aplicativo SSO de **Kerberos** ou **credencial** para **não configurado**.
  - **Credencial**: Use uma extensão de aplicativo de credencial genérica e personalizável para usar o SSO. Certifique-se de que você conhece a ID da extensão e a ID da equipe para a extensão do aplicativo de SSO da sua organização.  
  - **Kerberos**: Use a extensão Kerberos interna da Apple, que está incluída no macOS Catalina 10,15 e mais recente. Essa opção é uma versão específica do Kerberos da extensão do aplicativo de **credencial** .

  > [!TIP]
  > Com o tipo de **credencial** , você adiciona seus próprios valores de configuração para passar pela extensão. Em vez disso, considere o uso de definições de configuração internas fornecidas pela Apple no tipo **Kerberos** .

- **ID da extensão** (somente credencial): Insira o identificador do pacote que identifica a extensão do aplicativo SSO, como `com.apple.ssoexample`.
- **ID da equipe** (somente credencial): Insira o identificador de equipe de sua extensão de aplicativo SSO. Um identificador de equipe é uma cadeia de caracteres alfanuméricos de 10 caracteres (números e letras) gerada pela Apple, como `ABCDE12345`. 

  [Localize sua ID de equipe](https://help.apple.com/developer-account/#/dev55c3c710c) (abre o site da Apple) tem mais informações.

- **Realm**: Insira o nome do seu realm Kerberos. O nome do Realm deve estar em letras maiúsculas, como `CONTOSO.COM`. Normalmente, o nome do realm é o mesmo que o nome de domínio DNS, mas em letras maiúsculas.
- **Domínios**: Insira os nomes de domínio ou host dos sites que podem autenticar por meio do SSO. Por exemplo, se seu site for `mysite.contoso.com`, `mysite` será o nome do host e `contoso.com` será o nome de domínio. Quando os usuários se conectam a qualquer um desses sites, a extensão do aplicativo trata do desafio de autenticação. Essa autenticação permite que os usuários usem ID de face, Touch ID ou Apple pincode/senha para entrar.

  - Todos os domínios em sua extensão de aplicativo de logon único os perfis do Intune devem ser exclusivos. Não é possível repetir um domínio em nenhum perfil de extensão de aplicativo de logon, mesmo se você estiver usando tipos diferentes de extensões de aplicativo SSO.
  - Esses domínios não diferenciam maiúsculas de minúsculas.

- **Configuração adicional** (somente credencial): Insira dados específicos de extensão adicionais a serem passados para a extensão do aplicativo SSO:
  - **Chave de configuração**: Insira o nome do item que você deseja adicionar, como `user name`.
  - **Tipo de valor**: Insira o tipo de dados. As opções são:

    - Cadeia
    - Booliano: no **valor de configuração**, insira `True` ou `False`.
    - Inteiro: no **valor de configuração**, insira um número.
    
  - **Valor de configuração**: Insira os dados.
  
  - **Adicionar**: Selecione para adicionar suas chaves de configuração.

- **Uso** do conjunto de chaves (somente Kerberos): escolha **Bloquear** para impedir que as senhas sejam salvas e armazenadas no conjunto de chaves. **Não configurado** (padrão) permite que as senhas sejam salvas e armazenadas no conjunto de chaves.  
- **ID de face, ID de toque ou senha** (somente Kerberos): **exigir** força os usuários a inserir sua ID de face, Touch ID ou senha da Apple para entrar nos domínios que você adicionou. **Não configurado** (padrão) não exige que os usuários usem a biometria ou a senha para entrar.
- **Realm padrão** (somente Kerberos): escolha **habilitar** para definir o valor de **Realm** que você inseriu como o realm padrão. **Não configurado** (padrão) não define um realm padrão.

  > [!TIP]
  > - **Habilite** essa configuração se você estiver configurando várias extensões de aplicativo SSO do Kerberos em sua organização.
  > - **Habilite** essa configuração se você estiver usando vários territórios. Ele define o valor de **Realm** que você inseriu como o realm padrão.
  > - Se você tiver apenas um Realm, deixe-o **não configurado** (padrão).

- **Descoberta automática** (somente Kerberos): quando definido como **Bloquear**, a extensão Kerberos não usa automaticamente o LDAP e o DNS para determinar o nome do seu Active Directory site. **Não configurado** (padrão) permite que a extensão Localize automaticamente o nome do site Active Directory.
- **Alterações de senha** (somente Kerberos): **Bloquear** impede que os usuários alterem as senhas que eles usam para entrar nos domínios que você inseriu. **Não configurado** (padrão) permite alterações de senha.  
- **Sincronização de senha** (somente Kerberos): escolha **habilitar** para sincronizar as senhas locais de seus usuários com o Azure AD. **Não configurado** (padrão) desabilita a sincronização de senha para o Azure AD. Use essa configuração como alternativa ou backup para SSO. Essa configuração não funcionará se os usuários estiverem conectados com uma conta móvel da Apple.
- **Windows Server Active Directory complexidade de senha** (somente Kerberos): escolha **exigir** para forçar senhas de usuário para atender aos requisitos de complexidade de senha do Active Directory. Consulte a [senha deve atender aos requisitos de complexidade](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) para obter mais informações. **Não configurado** (padrão) não exige que os usuários atendam aos requisitos de senha do Active Directory.
- **Comprimento mínimo da senha** (somente Kerberos): Insira o número mínimo de caracteres que podem criar a senha de um usuário. **Não configurado** (padrão) não impõe um comprimento mínimo de senha aos usuários.
- **Limite de reutilização de senha** (somente Kerberos): Insira o número de novas senhas, de 1-24, que devem ser usadas até que uma senha anterior possa ser reutilizada no domínio. **Não configurado** (padrão) não impõe um limite de reutilização de senha.
- **Duração mínima da senha** (somente Kerberos): Insira o número de dias que uma senha deve ser usada no domínio antes que um usuário possa alterá-la. **Não configurado** (padrão) não impõe uma idade mínima de senhas antes que elas possam ser alteradas.
- **Notificação de expiração de senha** (somente Kerberos): Insira o número de dias antes que uma senha expire que os usuários são notificados de que sua senha expirará. **Não configurado** (padrão) usa `15` dias.
- **Expiração da senha** (somente Kerberos): Insira o número de dias antes que a senha do dispositivo deva ser alterada. **Não configurado** (padrão) significa que as senhas de usuário nunca expiram.
- **Nome da entidade de segurança** (somente Kerberos): Insira o nome de usuário da entidade de segurança Kerberos. Você não precisa incluir o nome do realm. Por exemplo, em `user@contoso.com`, `user` é o nome principal e `contoso.com` é o nome do realm.
- **Active Directory código do site** (somente Kerberos): Insira o nome do site do Active Directory que a extensão Kerberos deve usar. Talvez não seja necessário alterar esse valor, pois a extensão Kerberos pode localizar automaticamente o Active Directory código do site.
- **Nome do cache** (somente Kerberos): Insira o nome GSS (Generic Security Services) do cache Kerberos. É mais provável que você não precise definir esse valor.  
- **Mensagem de requisitos de senha** (somente Kerberos): Insira uma versão de texto dos requisitos de senha da sua organização que são mostrados aos usuários. A mensagem será mostrada se você não exigir os requisitos de complexidade de senha do Active Directory ou não inserir um comprimento mínimo da senha.  
- **IDs de pacote de aplicativo** (somente Kerberos): **adicione** os identificadores de pacote de aplicativo que devem usar o logon único em seus dispositivos. Esses aplicativos recebem acesso ao tíquete de concessão de tíquete Kerberos, ao tíquete de autenticação e autenticam usuários para serviços que eles estão autorizados a acessar.
- **Mapeamento de realm de domínio** (somente Kerberos): **adicione** os sufixos DNS de domínio que devem ser mapeados para seu Realm. Use essa configuração quando os nomes DNS dos hosts não corresponderem ao nome do realm. É mais provável que você não precise criar esse mapeamento de domínio para Realm personalizado.

## <a name="associated-domains"></a>Domínios associados

No Intune, você pode:

- Adicione muitas associações de aplicativo para domínio.
- Associe vários domínios ao mesmo aplicativo.

Esta funcionalidade aplica-se a:

- macOS 10,15 e mais recente

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **ID do aplicativo**: Insira o identificador do aplicativo a ser associado a um site. O identificador do aplicativo inclui a ID da equipe e uma ID do pacote: `TeamID.BundleID`.

  A ID da equipe é uma cadeia de caracteres alfanuméricos de 10 caracteres (letras e números) gerada pela Apple para seus desenvolvedores de aplicativos, como `ABCDE12345`. [Localize sua ID de equipe](https://help.apple.com/developer-account/#/dev55c3c710c)  (abre o site da Apple) tem mais informações.

  A ID do pacote identifica exclusivamente o aplicativo e normalmente é formatada na notação de nome de domínio reverso. Por exemplo, a ID do pacote do localizador é `com.apple.finder`. Para localizar a ID do pacote, use o AppleScript no terminal:

  `osascript -e 'id of app "ExampleApp"'`

- **Domínio**: Insira o domínio do site para associar a um aplicativo. O domínio inclui um tipo de serviço e um nome de host totalmente qualificado, como `webcredentials:www.contoso.com`.

  Você pode corresponder a todos os subdomínios de um domínio associado inserindo `*.` (um curinga de asterisco e um ponto) antes do início do domínio. O período é necessário. Os domínios exatos têm uma prioridade mais alta do que os domínios curinga. Portanto, os padrões de domínios pai serão correspondidos *se* uma correspondência não for encontrada no subdomínio totalmente qualificado.

  O tipo de serviço pode ser:

  - **authsrv**: extensão do aplicativo de logon único
  - **AppLink**: link universal
  - **webcredentials**: AutoPreenchimento de senha

- **Adicionar**: Selecione para adicionar seus aplicativos e domínios associados.

> [!TIP]
> Para solucionar problemas, em seu dispositivo macOS, abra **preferências do sistema** > **perfis**. Confirme se o perfil que você criou está na lista perfis de dispositivo. Se estiver listado, verifique se a **configuração de domínios associados** está no perfil e inclui a ID e os domínios de aplicativo corretos.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode configurar os recursos do dispositivo no [Ios](ios-device-features-settings.md).
