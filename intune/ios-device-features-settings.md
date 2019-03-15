---
title: definições de funcionalidade do dispositivo iOS no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver todas as definições para configurar os dispositivos iOS para AirPrint, layout do ecrã principal, notificação das aplicações, dispositivos partilhados, o início de sessão único e definições de filtro de conteúdo web no Microsoft Intune. Utilize estas definições num perfil de configuração do dispositivo para configurar os dispositivos iOS para utilizar estas funcionalidades de Apple diferentes na sua organização.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34f0869b46323606d69891c3761bfbc154f3b6a3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566629"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>definições de dispositivos iOS para utilizar recursos comuns do iOS no Intune

O Intune inclui algumas definições incorporadas para permitir que os utilizadores utilizem diferentes funcionalidades de Apple nos respetivos dispositivos de iOS. Por exemplo, os administradores podem controlar como os utilizadores do iOS utilizam impressoras com o AirPrint, adicionar as aplicações e pastas à dock e páginas no ecrã inicial, Mostrar notificações da aplicação, mostrar detalhes da etiqueta de ativo no ecrã de bloqueio, utilizar a autenticação de início de sessão única e autenticar os utilizadores com certificados.

Utilize estas funcionalidades para controlar os dispositivos iOS como parte da sua solução de gestão (MDM) de dispositivos móveis.

Este artigo apresenta uma lista essas configurações e descreve o que faz cada definição.

## <a name="before-you-begin"></a>Antes de começar

[Criar perfil de configuração de dispositivo um iOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint-settings"></a>Definições do AirPrint

Esta funcionalidade permite iOS, os usuários imprimam em impressoras conhecidas com o AirPrint.

1. Na **configurações**, selecione **AirPrint**. Introduza as seguintes propriedades do servidor AirPrint:

    - **Endereço IP**: Introduza o endereço IPv4 ou IPv6 da impressora. Se utilizar os nomes de anfitrião para identificar as impressoras, pode obter o endereço IP ao enviar pings para a impressora no terminal. Obtenha o endereço IP e o caminho (neste artigo) fornece mais detalhes.
    - **Caminho**: O caminho é normalmente `ipp/print` para impressoras na sua rede. Obtenha o endereço IP e o caminho (neste artigo) fornece mais detalhes.
    - **Porta**: Introduza a porta de escuta do destino AirPrint. Se deixar esta propriedade em branco, o AirPrint utiliza a porta predefinida. Disponível no iOS 11.0 e posterior.
    - **TLS**: Escolher **ativar** para proteger as ligações do AirPrint com Transport Layer Security (TLS). Disponível no iOS 11.0 e posterior.

2. Selecione **Adicionar**. O servidor do AirPrint é adicionado à lista. Pode adicionar vários servidores do AirPrint.

    Também pode **importação** um ficheiro separado por vírgulas (. csv) com essas informações. Depois de criar a lista, também pode **exportar** sua lista de servidores de AirPrint.

3. Quando terminar, selecione **OK** para guardar a sua lista.

Para adicionar servidores AirPrinter, terá do endereço IP da impressora, o caminho de recurso e a porta. Os passos seguintes mostram como obter estas informações.

1. Num Mac que está ligado à mesma rede local (sub-rede) que as impressoras do AirPrint, abra **Terminal** (partir **/Applications/Utilities**).
2. No Terminal, escreva `ippfind`, e selecione introduzir.

    Tenha em atenção as informações de impressora. Por exemplo, pode retornar algo semelhante à `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho de recurso.

3. No Terminal, escreva `ping myprinter.local`, e selecione introduzir.

   Tenha em atenção o endereço IP. Por exemplo, pode retornar algo semelhante à `PING myprinter.local (10.50.25.21)`.

4. Utilize os valores de caminho de recursos e o endereço IP. Neste exemplo, é o endereço IP `10.50.25.21`, e o caminho de recurso é `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Definições de esquema do ecrã principal

Estas definições configuram o esquema da aplicação e pastas na dock e telas iniciais de dispositivos iOS. Para utilizar esta funcionalidade, dispositivos iOS tem de estar no modo supervisionado e executam o iOS 9.3 ou posterior.

### <a name="dock"></a>Estação de ancoragem

Utilize o **encaixar** definições para adicionar até seis itens ou pastas à dock do ecrã iOS. Muitos dispositivos suportam menos itens. Por exemplo, os dispositivos iPhone suportam até quatro itens. Neste caso, apenas os primeiros quatro itens que adicione são apresentados no dispositivo.

1. Na **configurações**, selecione **esquema do ecrã principal (apenas supervisionado)** > **Dock** > **adicionar**. Pode adicionar até **seis** itens (aplicações e pastas combinadas) para a estação de ancoragem do dispositivo.
2. No **tipo**, escolha adicionar um **App** ou uma **pasta**.

    - **Adicionar uma aplicação**: Escolha esta opção para adicionar aplicações à estação de ancoragem na tela. Introduza:

      - **Nome da aplicação**: Introduza um nome para a aplicação. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
      - **ID do pacote de aplicação**: Introduza o ID do pacote da aplicação. Ver [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) para obter alguns exemplos.

      Selecione **OK** para guardar as alterações.

    - **Adicionar uma pasta**: Escolha esta opção para adicionar uma pasta à estação de ancoragem na tela. 

      Aplicações que adicionar a uma página numa pasta são dispostas da esquerda para a direita e na mesma ordem da lista. Se adicionar mais aplicações que aquelas que cabem numa página, estas serão movidas para outra página.

      1. Introduza um **nome da pasta**. Este nome é apresentado aos utilizadores nos respetivos dispositivos.
      2. Escolher **adicionar**e introduza as seguintes propriedades:

          - **Nome da página**: Introduza um nome para a página. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
          - **Nome da aplicação**: Introduza um nome para a aplicação. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
          - **ID do pacote de aplicação**: Introduza o ID do pacote da aplicação. Ver [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) para obter alguns exemplos.

      3. Selecione **Adicionar**. Pode adicionar até **20** páginas para o dispositivo da estação de ancoragem.
      4. Selecione **OK** para guardar as alterações.

#### <a name="example"></a>Exemplo

No exemplo a seguir, o ecrã de estação de ancoragem mostra apenas as aplicações Safari, correio e bolsa. A aplicação de correio está selecionada para mostrar as respetivas propriedades:

![Exemplo de definições da estação de ancoragem do iOS](./media/FfFiUcP.png)

Quando atribui a política a um iPhone, estação de ancoragem semelhante à seguinte imagem:

![Exemplo de esquema da estação de ancoragem do iOS no iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>Páginas

Adicione as páginas que pretende mostradas no ecrã principal e as aplicações que pretende mostrado em cada página. As aplicações que adicionar a uma página são dispostas da esquerda para a direita, pela mesma ordem como a lista. Se adicionar mais aplicações que aquelas que cabem numa página, estas serão movidas para outra página.

> [!TIP]
> Para reordenar os itens em quaisquer listas de páginas e ecrãs de página inicial, pode arrastar e soltá-los.

1. Na **configurações**, selecione **esquema do ecrã principal (apenas supervisionado)** > **páginas** > **adicionar**. Pode adicionar até **40** páginas num dispositivo.
2. Introduza um **nome da página**. Este nome é utilizado para sua referência no portal do Azure, e *não é* mostrado no dispositivo iOS. 

    Selecione **Adicionar**. Pode adicionar até **60** itens (aplicações e pasta combinados) num dispositivo.

3. No **tipo**, escolha adicionar um **App** ou uma **pasta**.

    - **Adicionar uma aplicação**: Escolha esta opção para adicionar aplicações para uma página na tela. Introduza:

      - **Nome da aplicação**: Introduza um nome para a aplicação. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
      - **ID do pacote de aplicação**: Introduza o ID do pacote da aplicação. Ver [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) para obter alguns exemplos.

      Selecione **OK** para guardar as alterações.

    - **Adicionar uma pasta**: Escolha esta opção para adicionar uma pasta à estação de ancoragem na tela. 

      Aplicações que adicionar a uma página numa pasta são dispostas da esquerda para a direita e na mesma ordem da lista. Se adicionar mais aplicações que aquelas que cabem numa página, estas serão movidas para outra página.

      1. Introduza um **nome da pasta**. Este nome é apresentado aos utilizadores nos respetivos dispositivos.
      2. Escolher **adicionar**e introduza as seguintes propriedades:

          - **Nome da página**: Introduza um nome para a página. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
          - **Nome da aplicação**: Introduza um nome para a aplicação. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo iOS.
          - **ID do pacote de aplicação**: Introduza o ID do pacote da aplicação. Ver [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) para obter alguns exemplos.

      3. Selecione **Adicionar**.
      4. Selecione **OK** para guardar as alterações.

#### <a name="example"></a>Exemplo

No exemplo seguinte, o nome de uma nova página **Contoso** é adicionado. A página mostra as aplicações encontrar amigos e definições. A aplicação de definições está selecionada para mostrar as respetivas propriedades:

![Exemplo de definições de Ecrã principal do iOS](./media/Jc2OxyX.png)

Quando atribui a política a um iPhone, a página será semelhante à seguinte imagem:

![Dispositivo iOS com o ecrã principal modificado](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Definições de notificações de aplicações

Escolha aplicações como instaladas nas notificações de envio de dispositivos iOS. Estas definições suportam dispositivos supervisionados com o iOS 9.3 e posterior.

1. Na **configurações**, selecione **notificações da aplicação (apenas supervisionado)** > **adicionar**:

    ![Adicionar notificação da aplicação no perfil de iOS no Intune](./media/ios-macos-app-notifications.png)

2. Introduza as seguintes propriedades:

    - **ID do pacote de aplicação**: Introduza o **ID do pacote de aplicação** da aplicação que pretende adicionar. Ver [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) para obter alguns exemplos.
    - **Nome da aplicação**: Introduza o nome da aplicação que pretende adicionar. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
    - **Publisher**: Introduza o publicador da aplicação que estiver a adicionar. Este nome é utilizado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
    - **Notificações**: **Ativar** ou **desativar** a aplicação a partir de envio de notificações no dispositivo.
       - **Mostrar no Centro de notificações**: **Ativar** permite que a aplicação mostre notificações no Centro de notificações do dispositivo. **Desativar** impede que a aplicação que mostra notificações no Centro de notificações.
       - **Mostrar no ecrã de bloqueio**: Selecione **ativar** para ver as notificações a partir da aplicação no ecrã de bloqueio do dispositivo. **Desativar** impede que a aplicação que mostra notificações no ecrã de bloqueio.
       - **Tipo de alerta**: Quando o dispositivo é desbloqueado em, escolha como a notificação é apresentada. As opções são:
         - **Nenhum**: Nenhuma notificação é apresentada.
         - **Faixa**: Uma faixa brevemente é mostrada com a notificação.
         - **Modal**: A notificação é apresentada e o utilizador tem a dispensar manualmente antes de continuar a utilizar o dispositivo.
       - **Distintivo no ícone da aplicação**: Selecione **ativar** para adicionar um distintivo ao ícone da aplicação. O destaque significa que a aplicação enviou uma notificação.
       - **Sons**: Selecione **ativar** para reproduzir um som quando for recebida uma notificação.

3. Selecione **OK** para guardar as alterações. Continue a adicionar as aplicações que pretende. Quando terminar, selecione **OK**.

## <a name="lock-screen-message-settings"></a>Definições de mensagem de ecrã de bloqueio

Utilize estas definições para mostrar uma mensagem personalizada ou de texto no ecrã de bloqueio e a janela de início de sessão. Por exemplo, pode introduzir uma mensagem "Se perdido, devolver a..." e informações de etiqueta de recursos. 

Esta funcionalidade suporta dispositivos supervisionados com o:

- iOS 9.3 e posterior

1. Na **configurações**, selecione **mensagem de ecrã de bloqueio (apenas supervisionado)**.
2. Introduza as seguintes definições:

    - **Informações da etiqueta de recursos**: Introduza as informações sobre a etiqueta de recursos do dispositivo. Por exemplo, introduza: `Owned by Contoso Corp` ou `Serial Number: {{serialnumber}}`. 

      O texto que introduzir é apresentado no ecrã de bloqueio e de janela no dispositivo de início de sessão.

    - **Nota de rodapé de ecrã de bloqueio**: Se o dispositivo é perdido ou roubado, introduza uma nota que poderá ajudar à devolução do dispositivo. Pode introduzir qualquer texto que pretende. Por exemplo, introduza algo como `If found, call Contoso at ...`.

    Tokens de dispositivo também podem ser utilizados para adicionar informações específicas do dispositivo para estes campos. Por exemplo, para mostrar o número de série, introduza `Serial Number: {{serialnumber}}`. No ecrã de bloqueio, o texto mostra semelhante `Serial Number 123456789ABC`. Ao introduzir as variáveis, não se esqueça de utilizar chavetas `{{ }}`. [Tokens de configuração de aplicação](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclui uma lista de variáveis que podem ser utilizados. Também pode utilizar `deviceName` ou qualquer outro valor específicos do dispositivo.

    > [!NOTE]
    > Variáveis não são validadas de interface do Usuário. Como resultado, poderá ver perfis salvos com entrada incorreta. Por exemplo, se introduzir `{{Devicename}}` em vez de `{{devicename}}`, em seguida, a cadeia literal é mostrada em vez do nome do dispositivo exclusivo.

3. Quando terminar, selecione **OK** para guardar as alterações.

## <a name="single-sign-on-settings"></a>Definições de início de sessão único

A maioria das aplicações de Linha de Negócio (LOB) exige algum nível de autenticação do utilizador para suportar a segurança. Em muitos casos, a autenticação requer que o utilizador introduzir as mesmas credenciais repetidamente, que é frustrante para os utilizadores. Para melhorar a experiência do usuário, os desenvolvedores podem criar aplicações que utilizam o início de sessão único (SSO). Utilizar o início de sessão único reduz o número de vezes que um utilizador tem de introduzir as credenciais.

Para utilizar o início de sessão único, certifique-se de que tem:

- Uma aplicação que é codificada para procurar o arquivo de credenciais de utilizador no início de sessão único no dispositivo.
- O Intune configurado para o início de sessão único em dispositivos iOS.

1. Na **configurações**, selecione **início de sessão único**:

   ![Painel Início de Sessão Único](./media/sso-blade.png)

2. Introduza as seguintes definições:

    - **Atributo de nome de utilizador do AAD**: Intune procura esse atributo para cada utilizador no Azure AD. Em seguida, o Intune preenche o campo (como o UPN) antes de gerar o XML que é instalado no dispositivo. As opções são:

      - **Nome principal de utilizador**: O UPN é analisado da seguinte forma:

        ![Atributo de nome de utilizador](media/User-name-attribute.png)

        Também pode substituir o âmbito pelo texto que introduzir na caixa de texto **Âmbito**.

        Por exemplo, a Contoso tiver várias regiões, incluindo a Europa, Ásia e América do Norte. Contoso, além dos utilizadores na Ásia para utilizar o SSO e a aplicação exige o UPN no `username@asia.contoso.com` formato. Quando seleciona **Nome Principal de utilizador**, o realm para cada utilizador é retirado do Azure AD, que é `contoso.com`. Portanto, para os utilizadores na Ásia, selecione **Nome Principal de utilizador**e introduza `asia.contoso.com`. Torna-se do UPN do utilizador final `username@asia.contoso.com`, em vez de `username@contoso.com`.

      - **ID de dispositivo do Intune**: Intune selecionará automaticamente o ID de dispositivo do Intune.

        Por predefinição, as aplicações só precisam de utilizar o ID do dispositivo. Mas se a sua aplicação utiliza o realm e o ID de dispositivo, pode escrever o realm na caixa de texto de Realm.

        > [!NOTE]
        > Por predefinição, mantenha o âmbito em branco se utilizar o ID do dispositivo.

      - **ID de dispositivo do Azure AD**

    - **Realm**: Introduza a parte do domínio do URL. Por exemplo, introduza `contoso.com`.
    - **Prefixos de URL que utilizarão o início de sessão único**: **Adicionar** todos os URLs na sua organização que necessitam de único início de sessão na autenticação de utilizador.

        Por exemplo, quando um utilizador se ligar a um destes sites, o dispositivo iOS utilizará as credenciais de início de sessão único. O utilizador não tem de introduzir credenciais adicionais. Se a autenticação multifator estiver ativada, os utilizadores têm de introduzir a segunda autenticação.

        > [!NOTE]
        > Estes URLs têm de ter um FQDN formatado adequadamente. Apple exige que estes estejam no `http://<yourURL.domain>` formato.

        Os padrões de correspondências do URL têm de começar com `http://` ou `https://`. Uma correspondência de cadeia de caracteres simples é executada, pelo que a `http://www.contoso.com/` prefixo de URL não corresponde ao `http://www.contoso.com:80/`. Com o iOS 10.0 ou posterior, um único caráter universal \* pode ser usado para inserir todos os valores correspondentes. Por exemplo, `http://*.contoso.com/` corresponde `http://store.contoso.com/` e `http://www.contoso.com`.

        O `http://.com` e `https://.com` padrões correspondem a todos os URLs HTTP e HTTPS, respetivamente.

    - **Aplicações que utilizarão o início de sessão único**: **Adicionar** aplicações em dispositivos dos utilizadores finais que podem utilizar o início de sessão único.

        O `AppIdentifierMatches` matriz tem de incluir as cadeias de caracteres que correspondam aos IDs de pacotes de aplicação. Estas cadeias devem ser correspondências exatas, tal como `com.contoso.myapp`, ou introduza uma correspondência de prefixo no ID do pacote com o \* caráter universal. O caráter universal tem de aparecer após um caráter de ponto final (.) e pode aparecer apenas uma vez, no final da cadeia de caracteres, como `com.contoso.*`. Quando um caráter universal é incluído, todas as aplicações cujo ID da coleção de pacotes começa com o prefixo têm acesso à conta.

        Utilize o **Nome da Aplicação** para introduzir um nome simples, para o ajudar a identificar o ID do pacote.

    - **Certificado de renovação de credencial**: Se utilizar certificados para autenticação (não palavras-passe), selecione o certificado SCEP ou PFX existente como o certificado de autenticação. Normalmente, este certificado é o mesmo certificado que é implementado para o utilizador para outros perfis, como VPN, Wi-Fi ou e-mail.

3. Quando terminar, selecione **OK** para guardar as alterações.

## <a name="web-content-filter-settings"></a>Definições de filtro de conteúdo Web

Estas definições controlam o acesso de URL do browser em dispositivos iOS.

1. Na **configurações**, selecione **filtro de conteúdo Web (apenas supervisionado)**.
2. Escolha o **tipo de filtro**. As opções são:

    - **Configurar URLs**: Utilize o filtro web incorporado da Apple que procura termos para adultos, incluindo palavras ofensivas e linguagem sexualmente explícita. Esta funcionalidade avalia cada página da web, como ele é carregado e identifica e bloquear conteúdo inadequado. Também pode adicionar URLs que pretende que não sejam verificados pelo filtro. Em alternativa, bloquear URLs específicos, independentemente das definições de filtro da Apple.

      - **URLs permitidos**: **Adicionar** os URLs que pretende permitir. Estes URLs ignorar o filtro da web da Apple.

        > [!NOTE]
        > Os URLs que introduzir são os URLs que não quer evauluated pelo filtro web da Apple. Estes URLs não são uma lista de sites permitidos. Para criar uma lista de Web sites autorizados, defina o **tipo de filtro** ao **apenas sites específicos**.

        Selecione **OK** para guardar as alterações.

      - **URLs bloqueados**: **Adicionar** os URLs que pretende parar de abertura, independentemente das definições de filtro da web da Apple.

        Selecione **OK** para guardar as alterações.

    - **Apenas sites específicos** (para o browser Safari apenas): Estes URLs são adicionados aos marcadores do browser Safari. O utilizador é **apenas** permissão para visitar estes sites; nenhum outro site pode ser aberto. Utilize esta opção apenas se souber a lista exata de URLs aos quais os utilizadores podem aceder.

      - **URL**: Introduza o URL do Web site que pretende permitir. Por exemplo, introduza `https://www.contoso.com`.
      - **Caminho do marcador**: Introduza o caminho para armazenar o marcador. Por exemplo, introduza `/Contoso/Business Apps`. Se não incluir um caminho, o marcador será adicionado à pasta de marcadores predefinida no dispositivo.
      - **Título**: Introduza um título descritivo para o marcador.

      Se não introduzir todos os URLs, em seguida, os utilizadores finais não podem aceder a sites, exceto para `microsoft.com`, `microsoft.net`, e `apple.com`. Estes URLs são automaticamente permitidas pelo Intune.

      Selecione **OK** para guardar as alterações.

## <a name="wallpaper-settings"></a>Definições de imagem de fundo

Adicione uma imagem personalizada do formato. png,. jpg ou. JPEG para os seus dispositivos iOS supervisionados. Por exemplo, utilize um logótipo de empresa no ecrã de bloqueio.

Poderá ter um comportamento inesperado quando um perfil com não existe nenhuma imagem for atribuído a dispositivos com uma imagem existente. Por exemplo, criar um perfil sem uma imagem. Este perfil é atribuído aos dispositivos que já têm uma imagem. Neste cenário, a imagem pode ser alterada para a predefinição do dispositivo ou a imagem original pode permanecer no dispositivo. Este comportamento é controlado e limitado pela plataforma de MDM da Apple.

- **Localização de exibição da imagem de fundo**: Escolha uma localização no dispositivo para mostrar a imagem. As opções são:
  - **Não configurado**: Uma imagem personalizada não é adicionada ao dispositivo. O dispositivo utiliza o padrão de sistema operativo.
  - **Ecrã de bloqueio**: Adiciona a imagem para o ecrã de bloqueio.
  - **Ecrã principal**: Adiciona a imagem ao ecrã principal.
  - **Bloqueio de ecrã e o ecrã principal**: Utiliza a mesma imagem da tela de bloqueio e o ecrã principal.
- **Imagem da imagem de fundo**: Carregar um existente. png,. jpg ou imagem JPEG que pretende utilizar. Certifique-se de que o tamanho do ficheiro é inferior a 750 KB. Também pode **remover** uma imagem que adicionou.

> [!TIP]
> Para exibir imagens diferentes da tela de bloqueio e o ecrã principal, crie um perfil com a imagem de ecrã de bloqueio. Crie outro perfil com a imagem de ecrã principal. Atribua ambos os perfis aos seus grupos de utilizadores ou dispositivos iOS.

## <a name="bundle-ids-for-built-in-ios-apps"></a>IDs de pacote para aplicações iOS incorporadas

A seguinte lista mostra o ID da coleção de pacotes de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software.

| ID do Pacote                   | Nome da Aplicação     | Fabricante |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendário     | Apple     |
| com.apple.camera            | Câmara       | Apple     |
| com.apple.mobiletimer       | Relógio        | Apple     |
| com.apple.compass           | Bússola      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Ficheiros        | Apple     |
| com.apple.mobileme.fmf1     | Encontrar Amigos | Apple     |
| com.apple.mobileme.fmip1    | Localizar iPhone  | Apple     |
| com.apple.gamecenter        | Centro de Jogos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Estado de Funcionamento       | Apple     |
| com.apple.Home              | Casa         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Correio         | Apple     |
| com.apple.Maps              | Maps         | Apple     |
| com.apple.MobileSMS         | Mensagens     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Notícias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotografias       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Lembretes    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Definições     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Bolsa       | Apple     |
| com.apple.tips              | Sugestões         | Apple     |
| com.apple.TV                | PROGRAMAS DE TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Meteorologia      | Apple     |

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar dispositivo perfis de funcionalidades para [macOS](macos-device-features-settings.md) dispositivos.
