---
title: configurações de recurso de dispositivo iOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja todas as configurações para configurar dispositivos iOS para impressão, layout das configurações de tela inicial, notificações de aplicativo, dispositivo compartilhado, logon único e filtro de conteúdo da Web em Microsoft Intune. Use essas configurações em um perfil de configuração de dispositivo para configurar dispositivos iOS para usar esses recursos da Apple em sua organização.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bac591a625fd915056234a75b26bc2f90f50cae7
ms.sourcegitcommit: 8023ba7d42e61bd37305c69f52a649cf83bf72e2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387102"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>configurações do dispositivo iOS para usar recursos comuns do iOS no Intune

O Intune inclui algumas configurações internas para permitir que os usuários do iOS usem recursos da Apple diferentes em seus dispositivos. Por exemplo, os administradores podem controlar como os usuários do iOS usam impressoras de impressão, adicionar aplicativos e pastas ao Dock e às páginas na tela inicial, Mostrar notificações do aplicativo, mostrar detalhes da marca do ativo na tela de bloqueio, usar autenticação de logon único e autenticar usuários com certificados.

Use esses recursos para controlar dispositivos iOS como parte da sua solução de MDM (gerenciamento de dispositivo móvel).

Este artigo lista essas configurações e descreve o que cada configuração faz.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo IOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint"></a>AirPrint

- **Endereço IP**: Insira o endereço IPv4 ou IPv6 da impressora. Se você usar nomes de host para identificar impressoras, poderá obter o endereço IP executando ping na impressora no terminal. Obter o endereço IP e o caminho (neste artigo) fornece mais detalhes.
- **Caminho**: O caminho é normalmente `ipp/print` para impressoras em sua rede. Obter o endereço IP e o caminho (neste artigo) fornece mais detalhes.
- **Porta**: Insira a porta de escuta do destino de impressão. Se você deixar essa propriedade em branco, o impresso usará a porta padrão. Disponível no iOS 11,0 e posterior.
- **TLS**: Escolha **habilitar** para proteger conexões de esprint com segurança de camada de transporte (TLS). Disponível no iOS 11,0 e posterior.

**Adicionar** adiciona o servidor de impressão para a lista. Muitos servidores de impressão de impressões podem ser adicionados. Você também pode **importar** um arquivo separado por vírgulas (. csv) com essas informações. **Exportar** cria uma lista dos servidores de impressão que você adicionou.

Selecione **OK** para salvar sua lista.

### <a name="get-server-ip-address-resource-path-and-port"></a>Obter endereço IP do servidor, caminho do recurso e porta

Para adicionar servidores do servidor de impressão, você precisa do endereço IP da impressora, do caminho do recurso e da porta. As etapas a seguir mostram como obter essas informações.

1. Em um Mac que está conectado à mesma rede local (sub-rede) que as impressoras de impressão impressa, abra o **terminal** (de **/Applications/Utilities**).
2. No terminal, digite `ippfind`e selecione Enter.

    Anote as informações da impressora. Por exemplo, ele pode retornar algo semelhante a `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho do recurso.

3. No terminal, digite `ping myprinter.local`e selecione Enter.

   Anote o endereço IP. Por exemplo, ele pode retornar algo semelhante a `PING myprinter.local (10.50.25.21)`.

4. Use os valores de caminho de recurso e endereço IP. Neste exemplo, o endereço IP é `10.50.25.21`e o caminho do recurso é. `/ipp/port1`

## <a name="home-screen-layout-settings"></a>Configurações de layout da tela inicial

Essas configurações configuram o layout do aplicativo e as pastas nas telas de Dock e Home dos dispositivos iOS. Para usar esse recurso, os dispositivos iOS devem estar no modo supervisionado e executar o iOS 9,3 ou posterior.

### <a name="dock"></a>Ancorá

Use as configurações de **encaixe** para adicionar até seis itens ou pastas ao Dock da tela do Ios. Muitos dispositivos dão suporte a menos itens. Por exemplo, os dispositivos iPhone dão suporte a até quatro itens. Nesse caso, somente os primeiros quatro itens que você adicionar serão mostrados no dispositivo.

Você pode adicionar até **seis** itens (aplicativos e pastas combinados) para o encaixe do dispositivo.

- **Adicionar**: Adiciona aplicativos ou pastas ao Dock no dispositivo.
- **Tipo**: Adicionar um **aplicativo** ou uma **pasta**:

  - **Aplicativo**: Escolha esta opção para adicionar aplicativos ao Dock na tela. Digita

    - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
    - **ID do pacote da aplicação**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

    Selecione **OK** para guardar as alterações.

  - **Pasta**: Escolha esta opção para adicionar uma pasta ao Dock na tela.

    Os aplicativos que você adiciona a uma página em uma pasta são organizados da esquerda para a direita e na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

    - **Nome da pasta**: Insira o nome da pasta. Esse nome é mostrado aos usuários em seu dispositivo.
    - **Lista de páginas**: **Adicione** uma página e insira as seguintes propriedades:

      - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
      - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
      - **ID do pacote da aplicação**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

      Você pode adicionar até **20** páginas para o encaixe do dispositivo.

    Selecione **OK** para guardar as alterações.

> [!NOTE]
> Quando você adiciona ícones usando as configurações de encaixe, os ícones na tela inicial e nas páginas são bloqueados e não podem ser movidos. Isso pode ser por design com as políticas de MDM do iOS e da Apple.

#### <a name="example"></a>Exemplo

No exemplo a seguir, a tela Dock mostra apenas os aplicativos Safari, mail e stocks. O aplicativo de email é selecionado para mostrar suas propriedades:

![Exemplo de definições da estação de ancoragem do iOS](./media/FfFiUcP.png)

Quando você atribui a política a um iPhone, o Dock é semelhante à imagem a seguir:

![Exemplo de esquema da estação de ancoragem do iOS no iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>Páginas

Adicione as páginas que você deseja mostrar na tela inicial e os aplicativos que você deseja mostrar em cada página. Os aplicativos que você adiciona a uma página são organizados da esquerda para a direita, na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

> [!TIP]
> Para reordenar os itens em qualquer lista de tela inicial e páginas, você pode arrastá-los e soltá-los.

Você pode adicionar até **40** páginas em um dispositivo.

- **Lista de páginas**: **Adicione** uma página e insira as seguintes propriedades:

  - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure e *não é* mostrado no dispositivo IOS.

  Você pode adicionar até **60** itens (aplicativos e pastas combinados) em um dispositivo.

  - **Adicionar**: Adiciona aplicativos ou pastas a uma página no dispositivo.

    - **Tipo**: Adicionar um **aplicativo** ou uma **pasta**:

      - **Aplicativo**: Escolha esta opção para adicionar aplicativos a uma página na tela. Introduza também:

        - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
        - **ID do pacote da aplicação**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

      Selecione **OK** para guardar as alterações.

      - **Pasta**: Escolha esta opção para adicionar uma pasta ao Dock na tela.

        Os aplicativos que você adiciona a uma página em uma pasta são organizados da esquerda para a direita e na mesma ordem que a lista. Se você adicionar mais aplicativos do que o pode caber em uma página, os aplicativos serão movidos para outra página.

        - **Nome da pasta**: Insira um nome para a pasta. Esse nome é mostrado aos usuários no dispositivo.
        - **Adicionar**: Adiciona páginas à pasta. Insira também as seguintes propriedades:

          - **Nome da página**: Insira um nome para a página. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
          - **Nome do aplicativo**: Insira um nome para o aplicativo. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo IOS.
          - **ID do pacote da aplicação**: Insira a ID do pacote do aplicativo. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.

      Selecione **OK** para guardar as alterações.

#### <a name="example"></a>Exemplo

No exemplo a seguir, uma nova página chamada **contoso** é adicionada. A página mostra os aplicativos localizar amigos e configurações. O aplicativo configurações é selecionado para mostrar suas propriedades:

![Exemplo de definições de Ecrã principal do iOS](./media/Jc2OxyX.png)

Quando você atribui a política a um iPhone, a página é semelhante à imagem a seguir:

![Dispositivo iOS com o ecrã principal modificado](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Configurações de notificações do aplicativo

Escolha como os aplicativos instalados em dispositivos iOS enviam notificações. Estas definições suportam dispositivos supervisionados com o iOS 9.3 e posterior.

- **Adicionar**: Adicionar notificações para aplicativos:

    ![Adicionar notificação de aplicativo no perfil do iOS no Intune](./media/ios-macos-app-notifications.png)

  - **ID do pacote de aplicativo**: Insira a **ID do pacote de aplicativo** do aplicativo que você deseja adicionar. Consulte [IDs de pacote para aplicativos Ios internos](bundle-ids-built-in-ios-apps.md) para ver alguns exemplos.
  - **Nome da aplicação**: Insira o nome do aplicativo que você deseja adicionar. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
  - **Publicador**: Insira o editor do aplicativo que você está adicionando. Esse nome é usado para sua referência no portal do Azure. Ele *não é* mostrado no dispositivo.
  - **Notificações**: **Habilitar** ou **desabilitar** o envio de notificações ao dispositivo pelo aplicativo.
    - **Mostrar no centro de notificações**: **Habilitar** permite que o aplicativo mostre notificações no centro de notificações do dispositivo. **Desabilitar** impede que o aplicativo mostre notificações no centro de notificações.
    - **Mostrar na tela de bloqueio**: Selecione **habilitar** para ver as notificações do aplicativo na tela de bloqueio do dispositivo. **Desabilitar** impede que o aplicativo mostre notificações na tela de bloqueio.
    - **Tipo de alerta**: Quando o dispositivo for desbloqueado de, escolha como a notificação é mostrada. As opções são:
      - **Nenhum**: Nenhuma notificação é mostrada.
      - **Faixa**: Uma faixa é mostrada brevemente com a notificação.
      - **Janela restrita**: A notificação é mostrada e o usuário deve descartá-la manualmente antes de continuar a usar o dispositivo.
    - **Crachá no ícone do aplicativo**: Selecione **habilitar** para adicionar um crachá ao ícone do aplicativo. O emblema significa que o aplicativo enviou uma notificação.
    - **Sons**: Selecione **habilitar** para tocar um som quando uma notificação for entregue.

Selecione **OK** para guardar as alterações.

## <a name="lock-screen-message-settings"></a>Configurações de mensagem da tela de bloqueio

Use essas configurações para mostrar uma mensagem personalizada ou um texto na janela de entrada e na tela de bloqueio. Por exemplo, você pode inserir um "se perdido, retornar para..." informações de marca de mensagem e de ativo. 

Esse recurso dá suporte a dispositivos supervisionados que executam o iOS 9,3 e posterior.

- **Informações de marca do ativo**: Insira informações sobre a marca de ativo do dispositivo. Por exemplo, introduza: `Owned by Contoso Corp` ou `Serial Number: {{serialnumber}}`.

  O texto inserido é mostrado na janela de entrada e na tela de bloqueio no dispositivo.

- **Nota de rodapé da tela de bloqueio**: Se o dispositivo for perdido ou roubado, insira uma observação que pode ajudar a obter o dispositivo retornado. Você pode inserir qualquer texto desejado. Por exemplo, introduza algo como `If found, call Contoso at ...`.

  Os tokens de dispositivo também podem ser usados para adicionar informações específicas do dispositivo a esses campos. Por exemplo, para mostrar o número de série, `Serial Number: {{serialnumber}}`digite. Na tela de bloqueio, o texto é exibido de `Serial Number 123456789ABC`forma semelhante a. Ao inserir variáveis, certifique-se de usar chaves `{{ }}`. Os tokens de [configuração de aplicativo](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) incluem uma lista de variáveis que podem ser usadas. Você também pode usar `deviceName` ou qualquer outro valor específico do dispositivo.

  > [!NOTE]
  > As variáveis não são validadas na interface do usuário e diferenciam maiúsculas de minúsculas. Como resultado, você poderá ver os perfis salvos com entrada incorreta. Por exemplo, se você inserir `{{DeviceID}}` em vez `{{deviceid}}`de, a cadeia de caracteres literal será mostrada em vez da ID exclusiva do dispositivo. Certifique-se de inserir as informações corretas.

Selecione **OK** para guardar as alterações.

## <a name="single-sign-on-settings"></a>Configurações de logon único

A maioria das aplicações de Linha de Negócio (LOB) exige algum nível de autenticação do utilizador para suportar a segurança. Em muitos casos, a autenticação exige que o usuário insira as mesmas credenciais repetidamente, o que é frustrante para os usuários. Para melhorar a experiência do usuário, os desenvolvedores podem criar aplicativos que usam SSO (logon único). O uso do logon único reduz o número de vezes que um usuário deve inserir as credenciais.

Para usar o logon único, verifique se você tem:

- Um aplicativo que é codificado para procurar o repositório de credenciais do usuário no logon único no dispositivo.
- O Intune configurado para o início de sessão único em dispositivos iOS.

![Painel Início de Sessão Único](./media/sso-blade.png)

- **Atributo de nome de usuário do AAD**: O Intune procura esse atributo para cada usuário no Azure AD. Em seguida, o Intune popula o respectivo campo (como o UPN) antes de gerar o XML que é instalado no dispositivo. As opções são:

  - **Nome principal do usuário**: O UPN é analisado da seguinte maneira:

    ![Atributo de nome de utilizador](media/User-name-attribute.png)

    Também pode substituir o âmbito pelo texto que introduzir na caixa de texto **Âmbito**.

    Por exemplo, a contoso tem várias regiões, incluindo Europa, Ásia e América do Norte. A contoso quer que seus usuários da Ásia usem o SSO, e o aplicativo requer o `username@asia.contoso.com` UPN no formato. Quando você seleciona **nome UPN**, o realm de cada usuário é obtido do Azure AD, que é `contoso.com`. Para usuários na Ásia, selecione **nome UPN**e digite `asia.contoso.com`. O UPN do usuário final se `username@asia.contoso.com`torna, em `username@contoso.com`vez de.

  - **ID do dispositivo do Intune**: O Intune seleciona automaticamente a ID do dispositivo do Intune.

    Por predefinição, as aplicações só precisam de utilizar o ID do dispositivo. Mas se seu aplicativo usar o realm e a ID do dispositivo, você poderá digitar o realm na caixa de texto realm.

    > [!NOTE]
    > Por predefinição, mantenha o âmbito em branco se utilizar o ID do dispositivo.

  - **ID do dispositivo do Azure AD**

- **Realm**: Insira a parte do domínio da URL. Por exemplo, introduza `contoso.com`.
- Prefixos de **URL que usarão o logon único**: **Adicione** qualquer URL em sua organização que exija autenticação de logon único do usuário.

  Por exemplo, quando um utilizador se ligar a um destes sites, o dispositivo iOS utilizará as credenciais de início de sessão único. O utilizador não tem de introduzir credenciais adicionais. Se a autenticação multifator estiver habilitada, os usuários serão solicitados a inserir a segunda autenticação.

  > [!NOTE]
  > Estes URLs têm de ter um FQDN formatado adequadamente. A Apple exige que eles estejam no `http://<yourURL.domain>` formato.

  Os padrões de correspondências do URL têm de começar com `http://` ou `https://`. Uma correspondência de cadeia de caracteres simples é executada `http://www.contoso.com/` , portanto, o `http://www.contoso.com:80/`prefixo da URL não corresponde. Com o Ios 10,0 ou posterior, um único \* curinga pode ser usado para inserir todos os valores correspondentes. Por exemplo, `http://*.contoso.com/` `http://store.contoso.com/` corresponde a e `http://www.contoso.com`a.

  Os `http://.com` padrões `https://.com` e correspondem a todas as URLs http e HTTPS, respectivamente.

- **Aplicativos que usarão o logon único**: **Adicionar** aplicativos nos dispositivos dos usuários finais que podem usar o logon único.

  A `AppIdentifierMatches` matriz deve incluir cadeias de caracteres que correspondam às IDs do pacote de aplicativo. Essas cadeias de caracteres podem ser correspondências `com.contoso.myapp`exatas, como ou inserir uma correspondência de prefixo na ID \* do pacote usando o caractere curinga. O caractere curinga deve aparecer após um caractere de ponto (.) e pode aparecer apenas uma vez, no final da cadeia de caracteres, como `com.contoso.*`. Quando um caráter universal é incluído, todas as aplicações cujo ID da coleção de pacotes começa com o prefixo têm acesso à conta.

  Utilize o **Nome da Aplicação** para introduzir um nome simples, para o ajudar a identificar o ID do pacote.

- **Certificado de renovação**de credencial: Se estiver usando certificados para autenticação (não senhas), selecione o certificado SCEP ou PFX existente como o certificado de autenticação. Normalmente, esse certificado é o mesmo certificado implantado para o usuário para outros perfis, como VPN, Wi-Fi ou email.

Selecione **OK** para guardar as alterações.

## <a name="web-content-filter-settings"></a>Configurações de filtro de conteúdo da Web

Essas configurações controlam o acesso à URL do navegador em dispositivos iOS supervisionados.

- **Tipo de filtro**: Escolha permitir sites específicos. As opções são:

  - **Configurar URLs**: Use o filtro da Web interno da Apple que procura termos adultos, incluindo linguagem obscena e sexualmente explícita. Esse recurso avalia cada página da Web conforme ela é carregada e identifica e bloqueia conteúdo inadequado. Você também pode adicionar URLs que não deseja que sejam verificadas pelo filtro. Ou, bloquear URLs específicas, independentemente das configurações de filtro da Apple.

    - **URLs permitidas**: **Adicione** as URLs que você deseja permitir. Essas URLs ignoram o filtro da Web da Apple.

      > [!NOTE]
        > As URLs inseridas são as URLs que você não deseja evauluated pelo filtro da Web da Apple. Essas URLs não são uma lista de sites permitidos. Para criar uma lista de sites permitidos, defina o **tipo** de filtro **somente para sites específicos**.

      Selecione **OK** para guardar as alterações.

    - **URLs bloqueadas**: **Adicione** as URLs que você deseja parar de abrir, independentemente das configurações do filtro da Web da Apple.

      Selecione **OK** para guardar as alterações.

  - **Somente sites específicos** (somente para o navegador da Web do Safari): Essas URLs são adicionadas aos indicadores do navegador Safari. O usuário **só** tem permissão para visitar esses sites; nenhum outro site pode ser aberto. Utilize esta opção apenas se souber a lista exata de URLs aos quais os utilizadores podem aceder.

    - **URL**: Insira a URL do site que você deseja permitir. Por exemplo, introduza `https://www.contoso.com`.
    - **Caminho do indicador**: Insira o caminho para armazenar o indicador. Por exemplo, introduza `/Contoso/Business Apps`. Se não incluir um caminho, o marcador será adicionado à pasta de marcadores predefinida no dispositivo.
    - **Título**: Insira um título descritivo para o indicador.

    Se você não inserir nenhuma URL, os usuários finais não poderão acessar nenhum site, `microsoft.com`exceto `microsoft.net`para, `apple.com`e. Essas URLs são permitidas automaticamente pelo Intune.

    Selecione **OK** para guardar as alterações.

## <a name="wallpaper-settings"></a>Configurações de papel de parede

Adicione uma imagem. png,. jpg ou. jpeg personalizada aos dispositivos iOS supervisionados. Por exemplo, use um logotipo da empresa na tela de bloqueio.

Você pode enfrentar um comportamento inesperado quando um perfil sem imagem é atribuído a dispositivos com uma imagem existente. Por exemplo, você cria um perfil sem uma imagem. Este perfil é atribuído a dispositivos que já têm uma imagem. Nesse cenário, a imagem pode mudar para o padrão do dispositivo ou a imagem original pode permanecer no dispositivo. Esse comportamento é controlado e limitado pela plataforma MDM da Apple.

- **Local de exibição do papel de parede**: Escolha um local no dispositivo para mostrar a imagem. As opções são:
  - **Não configurado**: Uma imagem personalizada não é adicionada ao dispositivo. O dispositivo usa o padrão do sistema operacional.
  - **Tela de bloqueio**: Adiciona a imagem à tela de bloqueio.
  - **Tela inicial**: Adiciona a imagem à tela inicial.
  - Tela **de bloqueio e página inicial**: Usa a mesma imagem na tela de bloqueio e na tela inicial.
- **Imagem do papel de parede**: Carregue uma imagem. png,. jpg ou. jpeg existente que você deseja usar. Verifique se o tamanho do arquivo é menor que 750 KB. Você também pode **remover** uma imagem que você adicionou.

> [!TIP]
> Para exibir imagens diferentes na tela de bloqueio e na tela inicial, crie um perfil com a imagem da tela de bloqueio. Crie outro perfil com a imagem da tela inicial. Atribua os dois perfis aos seus grupos de dispositivos ou usuários do iOS.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de recurso de dispositivo para dispositivos [MacOS](macos-device-features-settings.md) .
