---
title: configurações de recurso de dispositivo iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja todas as configurações para configurar dispositivos iOS para impressão, layout das configurações de tela inicial, notificações de aplicativo, dispositivo compartilhado, logon único e filtro de conteúdo da Web em Microsoft Intune. Use essas configurações em um perfil de configuração de dispositivo para configurar dispositivos iOS para usar esses recursos da Apple em sua organização.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
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
ms.openlocfilehash: e73612080e52c8eb49a0c090b68e917e24fef3ab
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992953"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>configurações do dispositivo iOS e iPadOS para usar recursos comuns do iOS no Intune

O Intune inclui algumas configurações internas para permitir que os usuários do iOS usem recursos da Apple diferentes em seus dispositivos. Por exemplo, os administradores podem controlar como os usuários do iOS usam impressoras de impressão, adicionar aplicativos e pastas ao Dock e às páginas na tela inicial, Mostrar notificações do aplicativo, mostrar detalhes da marca do ativo na tela de bloqueio, usar autenticação de logon único e autenticar usuários com certificados.

Use esses recursos para controlar dispositivos iOS como parte da sua solução de MDM (gerenciamento de dispositivo móvel).

Este artigo lista essas configurações e descreve o que cada configuração faz. Para obter mais informações sobre esses recursos, vá para [Adicionar configurações de recurso de dispositivo IOS ou MacOS](../device-features-configure.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo IOS](../device-features-configure.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro, com algumas configurações sendo aplicadas a todas as opções de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do IOS](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

> [!NOTE]
> Certifique-se de adicionar todas as impressoras ao mesmo perfil. A Apple impede que vários perfis de impressões sejam direcionados para o mesmo dispositivo.

- **Endereço IP**: Insira o endereço IPv4 ou IPv6 da impressora. Se você usar nomes de host para identificar impressoras, poderá obter o endereço IP executando ping na impressora no terminal. Obter o endereço IP e o caminho (neste artigo) fornece mais detalhes.
- **Caminho**: normalmente, o caminho é `ipp/print` para impressoras em sua rede. Obter o endereço IP e o caminho (neste artigo) fornece mais detalhes.
- **Porta**: Insira a porta de escuta do destino de impressão. Se você deixar essa propriedade em branco, o impresso usará a porta padrão. Disponível no iOS 11,0 e posterior.
- **TLS**: escolha **habilitar** para proteger conexões de esprint com segurança de camada de transporte (TLS). Disponível no iOS 11,0 e posterior.

Para adicionar servidores de impressão, você pode:

- **Adicionar** adiciona o servidor de impressão para a lista. Muitos servidores de impressão de impressões podem ser adicionados.
- **Importe** um arquivo separado por vírgulas (. csv) com essas informações. Ou, **Exportar** para criar uma lista de servidores de impressão que você adicionou.

### <a name="get-server-ip-address-resource-path-and-port"></a>Obter endereço IP do servidor, caminho do recurso e porta

Para adicionar servidores do servidor de impressão, você precisa do endereço IP da impressora, do caminho do recurso e da porta. As etapas a seguir mostram como obter essas informações.

1. Em um Mac que está conectado à mesma rede local (sub-rede) que as impressoras de impressão impressa, abra o **terminal** (de **/Applications/Utilities**).
2. No terminal, digite `ippfind`e selecione Enter.

    Anote as informações da impressora. Por exemplo, ele pode retornar algo semelhante a `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho do recurso.

3. No terminal, digite `ping myprinter.local`e selecione Enter.

   Anote o endereço IP. Por exemplo, ele pode retornar algo semelhante a `PING myprinter.local (10.50.25.21)`.

4. Use os valores de caminho de recurso e endereço IP. Neste exemplo, o endereço IP é `10.50.25.21`e o caminho do recurso é `/ipp/port1`.

## <a name="home-screen-layout"></a>Esquema do ecrã principal

Esta funcionalidade aplica-se a:

- iOS 9,3 ou mais recente

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

### <a name="dock"></a>Ancorá

Use as configurações de **encaixe** para adicionar até seis itens ou pastas ao Dock da tela do Ios. Muitos dispositivos dão suporte a menos itens. Por exemplo, os dispositivos iPhone dão suporte a até quatro itens. Nesse caso, somente os primeiros quatro itens que você adicionar serão mostrados no dispositivo.

Você pode adicionar até **seis** itens (aplicativos e pastas combinados) para o encaixe do dispositivo.

- **Adicionar**: Adiciona aplicativos ou pastas ao Dock no dispositivo.
- **Tipo**: adicionar um **aplicativo** ou uma **pasta**:

  - **Aplicativo**: escolha esta opção para adicionar aplicativos ao Dock na tela. introduza:

    - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
    - **ID do lote de aplicativos**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

  - **Pasta**: escolha esta opção para adicionar uma pasta ao Dock na tela.

    Os aplicativos que você adiciona a uma página em uma pasta são organizados da esquerda para a direita e na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

    - **Nome da pasta**: Insira o nome da pasta. Esse nome é mostrado aos usuários em seu dispositivo.
    - **Lista de páginas**: **adicione** uma página e insira as seguintes propriedades:

      - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
      - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
      - **ID do lote de aplicativos**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

      Você pode adicionar até **20** páginas para o encaixe do dispositivo.

> [!NOTE]
> Quando você adiciona ícones usando as configurações de encaixe, os ícones na tela inicial e nas páginas são bloqueados e não podem ser movidos. Isso pode ser por design com as políticas de MDM do iOS e da Apple.

#### <a name="example"></a>Exemplo

No exemplo a seguir, a tela Dock mostra apenas os aplicativos Safari, mail e stocks. O aplicativo de email é selecionado para mostrar suas propriedades:

![Exemplo de definições da estação de ancoragem do iOS](./media/ios-device-features-settings/FfFiUcP.png)

Quando você atribui a política a um iPhone, o Dock é semelhante à imagem a seguir:

![Exemplo de esquema da estação de ancoragem do iOS no iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Páginas

Adicione as páginas que você deseja mostrar na tela inicial e os aplicativos que você deseja mostrar em cada página. Os aplicativos que você adiciona a uma página são organizados da esquerda para a direita, na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

> [!TIP]
> Para reordenar os itens em qualquer lista de tela inicial e páginas, você pode arrastá-los e soltá-los.

Você pode adicionar até **40** páginas em um dispositivo.

- **Lista de páginas**: **adicione** uma página e insira as seguintes propriedades:

  - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure e *não é* mostrado no dispositivo IOS.

  Você pode adicionar até **60** itens (aplicativos e pastas combinados) em um dispositivo.

  - **Adicionar**: Adiciona aplicativos ou pastas a uma página no dispositivo.

    - **Tipo**: adicionar um **aplicativo** ou uma **pasta**:

      - **Aplicativo**: escolha esta opção para adicionar aplicativos a uma página na tela. Introduza também:

        - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
        - **ID do lote de aplicativos**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

      - **Pasta**: escolha esta opção para adicionar uma pasta ao Dock na tela.

        Os aplicativos que você adiciona a uma página em uma pasta são organizados da esquerda para a direita e na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

        - **Nome da pasta**: Insira um nome para a pasta. Esse nome é mostrado aos usuários no dispositivo.
        - **Adicionar**: Adiciona páginas à pasta. Insira também as seguintes propriedades:

          - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
          - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
          - **ID do lote de aplicativos**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

#### <a name="example"></a>Exemplo

No exemplo a seguir, uma nova página chamada **contoso** é adicionada. A página mostra os aplicativos localizar amigos e configurações. O aplicativo configurações é selecionado para mostrar suas propriedades:

![Exemplo de definições de Ecrã principal do iOS](./media/ios-device-features-settings/Jc2OxyX.png)

Quando você atribui a política a um iPhone, a página é semelhante à imagem a seguir:

![Dispositivo iOS com o ecrã principal modificado](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Notificações de aplicação

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Adicionar**: Adicionar notificações para aplicativos:

    ![Adicionar notificação de aplicativo no perfil do iOS no Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **ID do pacote de aplicativo**: Insira a **ID de lote** do aplicativo que você deseja adicionar. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.
  - **Nome do aplicativo**: Insira o nome do aplicativo que você deseja adicionar. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
  - **Editor**: Insira o editor do aplicativo que você está adicionando. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
  - **Notificações**: **habilite** ou **desabilite** o aplicativo de enviar notificações para o dispositivo.
    - **Mostrar no centro de notificações**: **habilitar** permite que o aplicativo mostre notificações no centro de notificações do dispositivo. **Desabilitar** impede que o aplicativo mostre notificações no centro de notificações.
    - **Mostrar na tela de bloqueio**: selecione **habilitar** para ver as notificações do aplicativo na tela de bloqueio do dispositivo. **Desabilitar** impede que o aplicativo mostre notificações na tela de bloqueio.
    - **Tipo de alerta**: quando o dispositivo for desbloqueado de, escolha como a notificação é mostrada. As opções são:
      - **Nenhum**: nenhuma notificação é mostrada.
      - **Faixa**: uma faixa é mostrada brevemente com a notificação.
      - **Modal**: a notificação é mostrada e o usuário deve descartá-la manualmente antes de continuar a usar o dispositivo.
    - **Notificação no ícone do aplicativo**: selecione **habilitar** para adicionar uma notificação ao ícone do aplicativo. O emblema significa que o aplicativo enviou uma notificação.
    - **Sons**: selecione **habilitar** para tocar um som quando uma notificação for entregue.

## <a name="lock-screen-message"></a>Mensagem da tela de bloqueio

Esta funcionalidade aplica-se a:

- iOS 9.3 e posterior

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Informações de marca do ativo**: Insira informações sobre a marca de ativo do dispositivo. Por exemplo, introduza: `Owned by Contoso Corp` ou `Serial Number: {{serialnumber}}`.

  O texto inserido é mostrado na janela de entrada e na tela de bloqueio no dispositivo.

- **Nota de rodapé da tela de bloqueio**: se o dispositivo for perdido ou roubado, insira uma observação que pode ajudar a obter o dispositivo retornado. Você pode inserir qualquer texto desejado. Por exemplo, introduza algo como `If found, call Contoso at ...`.

  Os tokens de dispositivo também podem ser usados para adicionar informações específicas do dispositivo a esses campos. Por exemplo, para mostrar o número de série, digite `Serial Number: {{serialnumber}}`. Na tela de bloqueio, o texto é exibido de forma semelhante a `Serial Number 123456789ABC`. Ao inserir variáveis, certifique-se de usar chaves `{{ }}`. Os [tokens de configuração de aplicativo](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) incluem uma lista de variáveis que podem ser usadas. Você também pode usar `deviceName` ou qualquer outro valor específico do dispositivo.

  > [!NOTE]
  > As variáveis não são validadas na interface do usuário e diferenciam maiúsculas de minúsculas. Como resultado, você poderá ver os perfis salvos com entrada incorreta. Por exemplo, se você inserir `{{DeviceID}}` em vez de `{{deviceid}}`, a cadeia de caracteres literal será mostrada em vez da ID exclusiva do dispositivo. Certifique-se de inserir as informações corretas.

## <a name="single-sign-on"></a>Início de sessão único

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Atributo de nome de utilizador do AAD**: o Intune procura este atributo para cada utilizador no Azure AD. Em seguida, o Intune popula o respectivo campo (como o UPN) antes de gerar o XML que é instalado no dispositivo. As opções são:

  - **Nome principal do usuário**: o UPN é analisado da seguinte maneira:

    ![Atributo de nome de utilizador](./media/ios-device-features-settings/User-name-attribute.png)

    Também pode substituir o âmbito pelo texto que introduzir na caixa de texto **Âmbito**.

    Por exemplo, a contoso tem várias regiões, incluindo Europa, Ásia e América do Norte. A contoso quer que seus usuários da Ásia usem o SSO, e o aplicativo requer o UPN no formato de `username@asia.contoso.com`. Quando você seleciona **nome UPN**, o realm de cada usuário é obtido do Azure AD, que é `contoso.com`. Portanto, para usuários na Ásia, selecione **nome UPN**e digite `asia.contoso.com`. O UPN do usuário final se torna `username@asia.contoso.com`, em vez de `username@contoso.com`.

  - **ID do dispositivo do Intune**: o Intune seleciona automaticamente a ID do dispositivo do Intune.

    Por predefinição, as aplicações só precisam de utilizar o ID do dispositivo. Mas se seu aplicativo usar o realm e a ID do dispositivo, você poderá digitar o realm na caixa de texto realm.

    > [!NOTE]
    > Por predefinição, mantenha o âmbito em branco se utilizar o ID do dispositivo.

  - **ID do dispositivo do Azure AD**

- **Realm**: Insira a parte do domínio da URL. Por exemplo, introduza `contoso.com`.
- **Prefixos de URL que vão utilizar o Início de Sessão Único**: **adicione** todos os URLs na sua organização que exigem a autenticação de início de sessão único do utilizador.

  Por exemplo, quando um utilizador se ligar a um destes sites, o dispositivo iOS utilizará as credenciais de início de sessão único. O utilizador não tem de introduzir credenciais adicionais. Se a autenticação multifator estiver habilitada, os usuários serão solicitados a inserir a segunda autenticação.

  > [!NOTE]
  > Estes URLs têm de ter um FQDN formatado adequadamente. A Apple exige que elas estejam no formato de `http://<yourURL.domain>`.

  Os padrões de correspondências do URL têm de começar com `http://` ou `https://`. Uma correspondência de cadeia de caracteres simples é executada, portanto, o prefixo de URL `http://www.contoso.com/` não corresponde `http://www.contoso.com:80/`. Com o iOS 10,0 ou posterior, um único curinga \* pode ser usado para inserir todos os valores correspondentes. Por exemplo, `http://*.contoso.com/` corresponde a `http://store.contoso.com/` e `http://www.contoso.com`.

  Os padrões de `http://.com` e `https://.com` correspondem a todas as URLs HTTP e HTTPS, respectivamente.

- **Aplicações que vão utilizar o Início de Sessão Único**: **adicione** aplicações a dispositivos dos utilizadores finais que podem utilizar o início de sessão único.

  A matriz de `AppIdentifierMatches` deve incluir cadeias de caracteres que correspondem às IDs do pacote de aplicativo. Essas cadeias de caracteres podem ser correspondências exatas, como `com.contoso.myapp`, ou inserir uma correspondência de prefixo na ID do pacote usando o caractere curinga \*. O caractere curinga deve aparecer após um caractere de ponto (.) e pode aparecer apenas uma vez, no final da cadeia de caracteres, como `com.contoso.*`. Quando um caráter universal é incluído, todas as aplicações cujo ID da coleção de pacotes começa com o prefixo têm acesso à conta.

  Utilize o **Nome da Aplicação** para introduzir um nome simples, para o ajudar a identificar o ID do pacote.

- **Certificado de renovação de credenciais**: se estiver usando certificados para autenticação (não senhas), selecione o certificado SCEP ou pfx existente como o certificado de autenticação. Normalmente, esse certificado é o mesmo certificado implantado para o usuário para outros perfis, como VPN, Wi-Fi ou email.

## <a name="web-content-filter"></a>Filtro de conteúdo da Web

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Tipo de filtro**: escolha permitir sites específicos. As opções são:

  - **Configurar URLs**: Use o filtro da Web interno da Apple que procura termos adultos, incluindo linguagem obscena e sexualmente explícita. Esse recurso avalia cada página da Web conforme ela é carregada e identifica e bloqueia conteúdo inadequado. Você também pode adicionar URLs que não deseja que sejam verificadas pelo filtro. Ou, bloquear URLs específicas, independentemente das configurações de filtro da Apple.

    - **URLs permitidas**: **adicione** as URLs que você deseja permitir. Essas URLs ignoram o filtro da Web da Apple.

        > [!NOTE]
        > As URLs inseridas são as URLs que você não deseja evauluated pelo filtro da Web da Apple. Essas URLs não são uma lista de sites permitidos. Para criar uma lista de sites permitidos, defina o **tipo** de filtro **somente para sites específicos**.

    - **URLs bloqueadas**: **adicione** as URLs que você deseja parar de abrir, independentemente das configurações do filtro da Web da Apple.

  - **Somente sites específicos** (somente para o navegador da Web do Safari): essas URLs são adicionadas aos indicadores do navegador Safari. O usuário **só** tem permissão para visitar esses sites; nenhum outro site pode ser aberto. Utilize esta opção apenas se souber a lista exata de URLs aos quais os utilizadores podem aceder.

    - **URL**: Insira a URL do site que você deseja permitir. Por exemplo, introduza `https://www.contoso.com`.
    - **Caminho do indicador**: a Apple alterou essa configuração. Todos os indicadores vão para a pasta **sites aprovados** . Os indicadores não entram no caminho do indicador que você inserir.
    - **Título**: Insira um título descritivo para o indicador.

    Se você não inserir nenhuma URL, os usuários finais não poderão acessar nenhum site, exceto `microsoft.com`, `microsoft.net`e `apple.com`. Essas URLs são permitidas automaticamente pelo Intune.

## <a name="single-sign-on-app-extension"></a>Extensão do aplicativo de logon único

Esta funcionalidade aplica-se a:

- iOS 13,0 e posterior
- iPadOS 13,0 e posterior

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Tipo de extensão do aplicativo SSO**: escolha o tipo de extensão do aplicativo SSO. As opções são:

  - **Não configurado**: as extensões de aplicativo não são usadas. Para desabilitar uma extensão de aplicativo, você pode alternar o tipo de extensão do aplicativo SSO para **não configurado**.
  - **Redirecionar**: Use uma extensão de aplicativo de redirecionamento genérica e personalizável para executar o SSO com fluxos de autenticação modernos. Certifique-se de que você conhece a ID de extensão para a extensão de aplicativo da sua organização.
  - **Credencial**: Use uma extensão de aplicativo de credencial genérica e personalizável para executar o SSO com fluxos de autenticação de desafio e resposta. Certifique-se de que você conhece a ID de extensão para a extensão de aplicativo da sua organização.
  - **Kerberos**: Use a extensão Kerberos interna da Apple, que está incluída no Ios 13,0 (e mais recente) e iPadOS 13,0 (e mais recente). Essa opção é uma versão específica do Kerberos da extensão do aplicativo de **credencial** .

  > [!TIP]
  > Com os tipos de **redirecionamento** e de **credencial** , você adiciona seus próprios valores de configuração para passar pela extensão. Se você estiver usando **credenciais**, considere o uso de definições de configuração internas fornecidas pela Apple no tipo **Kerberos** .

- **ID da extensão** (redirecionamento e credencial): Insira o identificador do pacote que identifica a extensão do aplicativo SSO, como `com.apple.extensiblesso`.

- **ID da equipe** (redirecionamento e credencial): Insira o identificador de equipe da sua extensão de aplicativo SSO. Um identificador de equipe é uma cadeia de caracteres alfanuméricos de 10 caracteres (números e letras) gerada pela Apple, como `ABCDE12345`. A ID da equipe não é necessária.

  [Localize sua ID de equipe](https://help.apple.com/developer-account/#/dev55c3c710c) (abre o site da Apple) tem mais informações.

- **Realm** (Credential e Kerberos): Insira o nome do seu Realm de autenticação. O nome do Realm deve estar em letras maiúsculas, como `CONTOSO.COM`. Normalmente, o nome do realm é o mesmo que o nome de domínio DNS, mas em letras maiúsculas.

- **Domínios** (credencial e Kerberos): Insira os nomes de domínio ou de host dos sites que podem ser autenticados por meio do SSO. Por exemplo, se seu site for `mysite.contoso.com`, `mysite` será o nome do host e `contoso.com` será o nome de domínio. Quando os usuários se conectam a qualquer um desses sites, a extensão do aplicativo trata do desafio de autenticação. Essa autenticação permite que os usuários usem ID de face, Touch ID ou Apple pincode/senha para entrar.

  - Todos os domínios em sua extensão de aplicativo de logon único os perfis do Intune devem ser exclusivos. Não é possível repetir um domínio em nenhum perfil de extensão de aplicativo de logon, mesmo se você estiver usando tipos diferentes de extensões de aplicativo SSO.
  - Esses domínios não diferenciam maiúsculas de minúsculas.

- **URLs** (somente redirecionamento): Insira os prefixos de URL de seus provedores de identidade em cujo nome a extensão do aplicativo de redirecionamento executa o SSO. Quando um usuário é redirecionado para essas URLs, a extensão do aplicativo SSO será intermediária e avisará o SSO.

  - Todas as URLs em seus perfis de extensão do aplicativo de logon único do Intune devem ser exclusivas. Não é possível repetir um domínio em nenhum perfil de extensão de aplicativo SSO, mesmo que você esteja usando tipos diferentes de extensões de aplicativo SSO.
  - As URLs devem começar com http://ou https://.

- **Configuração adicional** (redirecionamento e credencial): Insira dados específicos de extensão adicionais a serem passados para a extensão do aplicativo SSO:
  - **Chave**: Insira o nome do item que você deseja adicionar, como `user name`.
  - **Tipo**: Insira o tipo de dados. As opções são:

    - Cadeia
    - Booliano: no **valor de configuração**, insira `True` ou `False`.
    - Inteiro: no **valor de configuração**, insira um número.
    
  - **Valor**: Insira os dados.

  - **Adicionar**: Selecione para adicionar suas chaves de configuração.

- **Uso** do conjunto de chaves (somente Kerberos): escolha **Bloquear** para impedir que as senhas sejam salvas e armazenadas no conjunto de chaves. **Não configurado** (padrão) permite que as senhas sejam salvas e armazenadas no conjunto de chaves.
- **ID de face, ID de toque ou senha** (somente Kerberos): **exigir** força os usuários a inserir sua ID de face, Touch ID ou senha da Apple para entrar nos domínios que você adicionou. **Não configurado** (padrão) não exige que os usuários usem a biometria ou a senha para entrar.
- **Realm padrão** (somente Kerberos): escolha **habilitar** para definir o valor de **Realm** que você inseriu como o realm padrão. **Não configurado** (padrão) não define um realm padrão.

  > [!TIP]
  > - **Habilite** essa configuração se você estiver configurando várias extensões de aplicativo SSO do Kerberos em sua organização.
  > - **Habilite** essa configuração se você estiver usando vários territórios. Ele define o valor de **Realm** que você inseriu como o realm padrão.
  > - Se você tiver apenas um Realm, deixe-o **não configurado** (padrão).

- **Nome da entidade de segurança** (somente Kerberos): Insira o nome de usuário da entidade de segurança Kerberos. Você não precisa incluir o nome do realm. Por exemplo, em `user@contoso.com`, `user` é o nome principal e `contoso.com` é o nome do realm.

  > [!TIP]
  > - Você também pode usar variáveis no nome da entidade de segurança digitando chaves `{{ }}`. Por exemplo, para mostrar o nome de usuário, digite `Username: {{username}}`. 
  > - No entanto, tenha cuidado com a substituição de variáveis porque as variáveis não são validadas na interface do usuário e diferenciam maiúsculas de minúsculas. Certifique-se de inserir as informações corretas.

- **Active Directory código do site** (somente Kerberos): Insira o nome do site do Active Directory que a extensão Kerberos deve usar. Talvez não seja necessário alterar esse valor, pois a extensão Kerberos pode localizar automaticamente o Active Directory código do site.
- **Nome do cache** (somente Kerberos): Insira o nome GSS (Generic Security Services) do cache Kerberos. É mais provável que você não precise definir esse valor.
- **IDs de pacote de aplicativo** (somente Kerberos): **adicione** os identificadores de pacote de aplicativo que devem usar o logon único em seus dispositivos. Esses aplicativos recebem acesso ao tíquete de concessão de tíquete Kerberos, ao tíquete de autenticação e autenticam usuários para serviços que eles estão autorizados a acessar.
- **Mapeamento de realm de domínio** (somente Kerberos): **adicione** os sufixos DNS de domínio que devem ser mapeados para seu Realm. Use essa configuração quando os nomes DNS dos hosts não corresponderem ao nome do realm. É mais provável que você não precise criar esse mapeamento de domínio para Realm personalizado.
- **Certificado PKINIT** (somente Kerberos): **selecione** o certificado de autenticação de chave pública (PKINIT) que pode ser usado para autenticação Kerberos. Você pode escolher entre os certificados [PKCS](../protect/certficates-pfx-configure.md) ou [SCEP](../protect/certificates-scep-configure.md) que você adicionou no Intune. Para obter mais informações sobre certificados, consulte [usar certificados para autenticação no Microsoft Intune](../protect/certificates-configure.md).

## <a name="wallpaper"></a>Imagem de Fundo

Você pode enfrentar um comportamento inesperado quando um perfil sem imagem é atribuído a dispositivos com uma imagem existente. Por exemplo, você cria um perfil sem uma imagem. Este perfil é atribuído a dispositivos que já têm uma imagem. Nesse cenário, a imagem pode mudar para o padrão do dispositivo ou a imagem original pode permanecer no dispositivo. Esse comportamento é controlado e limitado pela plataforma MDM da Apple.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Local de exibição do papel de parede**: escolha um local no dispositivo para mostrar a imagem. As opções são:
  - **Não configurado**: uma imagem personalizada não é adicionada ao dispositivo. O dispositivo usa o padrão do sistema operacional.
  - **Tela de bloqueio**: adiciona a imagem à tela de bloqueio.
  - **Tela inicial**: adiciona a imagem à tela inicial.
  - Tela **de bloqueio e página inicial**: usa a mesma imagem na tela de bloqueio e na tela inicial.
- **Imagem de papel de parede**: carregue uma imagem. png,. jpg ou. jpeg existente que você deseja usar. Verifique se o tamanho do arquivo é menor que 750 KB. Você também pode **remover** uma imagem que você adicionou.

> [!TIP]
> Para exibir imagens diferentes na tela de bloqueio e na tela inicial, crie um perfil com a imagem da tela de bloqueio. Crie outro perfil com a imagem da tela inicial. Atribua os dois perfis aos seus grupos de dispositivos ou usuários do iOS.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Você também pode criar perfis de recurso de dispositivo para dispositivos [MacOS](macos-device-features-settings.md) .
