---
title: "Definições de restrições de dispositivos do Intune para iOS | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba que definições do Intune pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 2b8bf6d3944f9968d0f4020fbb5c57ef8180062c
ms.lasthandoff: 02/16/2017


---

# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos iOS no Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Geral
-     **Câmara** – Selecione se a câmara do dispositivo pode ser utilizada.     
-     **Submissão de dados de diagnóstico** – Permita ou impeça que o dispositivo submeta dados de diagnóstico à Apple.
-     **FaceTime** – Permita que a aplicação FaceTime seja utilizada no dispositivo.
-     **Captura de ecrã** – Permita ao utilizador capturar o conteúdo do ecrã como uma imagem.
-     **Siri** – Permita a utilização do assistente de voz Siri no dispositivo.
    -     **Siri enquanto o dispositivo está bloqueado** – Permita a utilização do assistente de voz Siri no dispositivo enquanto está bloqueado.
    -     **Filtro de linguagem inapropriada da Siri (apenas supervisionado)** – Impede que a Siri dite ou fale com linguagem inapropriada.
    -     **A Siri pode consultar conteúdos gerados pelo utilizador a partir da Internet (apenas supervisionado)** – Permita que a Siri aceda a sites para responder a perguntas.
-     **Certificados TLS não fidedignos** – Permita certificados Transport Layer Security não fidedignos no dispositivo.
-     **Acesso ao Centro de Controlo enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda ao centro de controlo quando o dispositivo está bloqueado.
-     **Notificações enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda à vista de notificações sem desbloquear o dispositivo.
-     **Passbook enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda à aplicação Passbook enquanto o dispositivo está bloqueado.
-     **Vista Hoje enquanto o dispositivo está bloqueado** – Permita que o utilizador veja a vista Hoje enquanto o dispositivo está bloqueado.
-     **Fidedignidade da aplicação empresarial** – Permite que o utilizador opte por confiar em aplicações que não foram transferidas a partir da loja de aplicações.
-     **AirDrop (apenas supervisionado)** – Permitir a utilização da funcionalidade AirDrop para trocar conteúdos com dispositivos que se encontrem próximos.
-     **A pesquisa Spotlight pode devolver resultados da Internet (apenas supervisionado)** – Permita que a pesquisa Spotlight se ligue à Internet para proporcionar mais resultados.
-     **Pesquisa de definição de palavras (apenas supervisionado)** – Permita a funcionalidade do iOS que permite realçar uma palavra e procurar a definição dela.
-     **Teclados preditivos (apenas supervisionado)** – Permita a utilização de teclados preditivos que sugerem palavras que o utilizador poderá querer utilizar.
-     **Correção automática (apenas supervisionado)** – Permite que o dispositivo corrija automaticamente palavras com erros ortográficos.
-     **Verificação ortográfica do teclado (apenas supervisionado)** – Permite o corretor ortográfico do dispositivo.
-     **Atalhos de teclado (apenas supervisionado)** – Permite a utilização de atalhos de teclado.
-     **Deteção de pulso para Apple Watch emparelhado** – Quando ativada, o Apple Watch não apresenta notificações quando não estiver a ser utilizado.
- **Pedir palavra-passe de emparelhamento para pedidos do AirPlay a enviar** – Exija uma palavra-passe de emparelhamento quando o utilizador utiliza o AirPlay para a transmissão de conteúdo para outros dispositivos da Apple.
- **Modificação da conta (apenas supervisionado)** – Permita que o utilizador alterar as definições de conta, tais como configurações de e-mail.
- **Emparelhamento com Apple Watch (apenas supervisionado)** – Permita que o dispositivo se emparelhe com um Apple Watch.
- **Modificação de Bluetooth (apenas supervisionado)** – Não permita que o utilizador final altere as definições de Bluetooth no dispositivo.
- **Observação remota do ecrã através da aplicação Classroom (apenas supervisionado)** – Permita ou bloqueie a observação do ecrã em dispositivos remotos por parte da aplicação de sala de aulas.
- **Ativar restrições nas definições do dispositivo (apenas supervisionado)** – Permita que o utilizador configure as restrições de dispositivo (restrições de acesso) no dispositivo.
- **Utilização da opção Apagar todos os conteúdos e definições no dispositivo (apenas supervisionado)** – Permita que o utilizador utilize a opção de apagar todo o conteúdo e definições no dispositivo.
- **Modificação do nome do dispositivo (apenas supervisionado)** – Permita que o utilizador altere o nome do dispositivo.
- **Modificação das definições da submissão de diagnósticos (apenas supervisionado)** – Permita ou bloqueie a submissão de dados de diagnóstico à Apple por parte do dispositivo.
- **Emparelhamento de anfitriões para controlar os dispositivos com que um dispositivo iOS se pode emparelhar (apenas supervisionado)** – Permita o emparelhamento de anfitriões para permitir que o administrador tenha controlo sobre os dispositivos com os quais um dispositivo iOS pode ser emparelhado.
- **Modificação das definições de notificação (apenas supervisionado)** – Permita que o utilizador altere as definições de notificação do dispositivo.
- **Modificação do código de acesso (apenas supervisionado)** – Permita que a palavra-passe do dispositivo seja adicionada, alterada ou removida.
- **Modificação da imagem de fundo (apenas supervisionado)** – Permita que o utilizador altere a imagem de fundo do dispositivo.
- **Modificação das definições de fidedignidade de aplicações empresariais (apenas supervisionado)** – Permite que o utilizador opte por confiar em aplicações que não foram transferidas a partir da loja de aplicações.
- **Instalar aplicações a partir da App Store (apenas supervisionado)** – Permita que o dispositivo aceda à App Store e instale aplicações.
- **Alterações às definições da aplicação Encontrar Amigos (apenas supervisionado)** – Permita que o utilizador altere as definições da aplicação Encontrar Amigos.
- **Loja iBooks (apenas supervisionado)** – Permita que o utilizador procure e compre livros da loja iBooks.
- **Aplicação Mensagens no dispositivo (apenas supervisionado)** – Permita a utilização da aplicação Mensagens para enviar e ler mensagens SMS.
- **Podcasts (apenas supervisionado)** – Permita a utilização da aplicação Podcasts.
- **Serviço Music (apenas supervisionado)** – Permita a utilização da aplicação Apple Music.
- **Serviço iTunes Radio (apenas supervisionado)** – Permita a utilização da aplicação iTunes Radio.
- **Apple News (apenas supervisionado)** – Permita a utilização da aplicação Apple News.
- **Alterações do perfil de configuração** – Permita que o utilizador instale perfis de configuração.

## <a name="password"></a>Palavra-passe
-     **Palavra-passe obrigatória** – Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
-     **Palavras-passe simples** – Permita palavras-passe simples, como 0000 e 1234.
-     **Tipo obrigatório de palavra-passe** – Especifique o tipo de palavra-passe que será obrigatório, como apenas numérica ou alfanumérica.
-     **Número de carateres não-alfanuméricos na palavra-passe** – Especifique o número de carateres de símbolos (como **#** ou **@**) que tem de ser incluído na palavra-passe.
-     **Comprimento mínimo da palavra-passe** – Especifique o número mínimo de carateres na palavra-passe.
-     **Número de falhas de início de sessão antes de limpar o dispositivo** – Especifique o número de tentativas de início de sessão falhadas antes desta definição eliminar os dados do dispositivo.
-     **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**<sup>1</sup> – Especifique durante quanto tempo o dispositivo pode permanecer inativo antes de o utilizador ter de reintroduzir a palavra-passe.
-     **Máximo de minutos de inatividade até o ecrã ser bloqueado**<sup>1</sup> – Especifique o número de minutos antes de o ecrã do dispositivo se desligar.
-     **Expiração de palavra-passe (dias)** – Especifique o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
-     **Impedir a reutilização de palavras-passe anteriores** – Especifique o número de palavras-passe utilizadas anteriormente que o dispositivo possa ter memorizado.
-     **Desbloqueio por impressão digital** – Permita a utilização de uma impressão digital para desbloquear dispositivos compatíveis.

<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos


-   **Loja de aplicações (apenas supervisionado)** – Bloqueie o acesso à loja de aplicações em dispositivos supervisionados.
-     **Palavra-passe para aceder à loja de aplicações** – Exija ao utilizador que introduza uma palavra-passe antes de poder visitar a loja de aplicações.
-     **Compras via aplicação** – Permita que se façam compras na loja a partir de uma aplicação em execução.
-     **Transferências automáticas de aplicações (apenas supervisionado)** -
-     **Conteúdo de música, podcast ou notícias explícito do iTunes (apenas supervisionado)** – Permita que o dispositivo aceda ao conteúdo classificado como para adultos a partir da loja.
-     **Transferir conteúdos da iBook store identificados como “Erótico”** – Permita que o utilizador transfira livros com a categoria “Erótico”.
-     **Ver documentos empresariais em aplicações não geridas** – Permita que os documentos empresariais sejam vistos em qualquer aplicação.<br>**Exemplo:** pretende impedir que os utilizadores guardem os ficheiros da aplicação OneDrive para a Dropbox. Configure esta definição como não. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não será permitido guardar.
-     **Ver documentos não empresariais em aplicações empresariais** – Permita que qualquer documento seja visto em aplicações empresariais geridas.
-     **Tratar o AirDrop como um destino não gerido** – Impede que as aplicações geridas possam enviar dados através do Airdrop.
-     **Adicionar amigos do Centro de Jogos (apenas supervisionado)** – Permita que o utilizador adicione amigos no Centro de Jogos.
-     **Centro de Jogos (apenas supervisionado)** – Bloqueie ou ative a utilização da aplicação do Centro de Jogos.
-     **Jogos de multijogadores (apenas supervisionado)** – Permita que o utilizador jogue jogos de multijogadores no dispositivo.
-     **Região das classificações** – Selecione a região das classificações para a qual quer configurar transferências permitidas e, em seguida, escolha as classificações permitidas para **Filmes** e **Programas de TV**.
-     **Aplicações** – Selecione a classificação etária permitida das aplicações que os utilizadores poderão transferir ou pode escolher **Permitir Todas as Aplicações**.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.
Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações, utilize o seguinte formato:

Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.
Copie o URL da página e utilize-o como o URL para configurar a lista das aplicações permitidas ou proibidas ou uma aplicação que pretende executar no modo de local público.
Os perfis de dispositivo que contêm as definições de aplicações restritas têm de ser implementados em grupos de utilizadores.

Exemplo: procure Microsoft Word para iPad. O URL que irá utilizar será https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Também pode utilizar o software iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.



### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.

## <a name="show-or-hide-apps"></a>Mostrar ou ocultar aplicações

Na lista mostrar ou ocultar aplicações, pode configurar uma das seguintes listas (requer dispositivos supervisionados com iOS 9.3 ou posterior).

Uma lista de **Aplicações ocultas** – Especifique uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
Uma lista de **Aplicações visíveis** – Especifique uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações, utilize o seguinte formato:

Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.
Copie o URL da página e utilize-o como o URL para configurar a lista das aplicações permitidas ou proibidas ou uma aplicação que pretende executar no modo de local público.

Exemplo: procure Microsoft Word para iPad. O URL que irá utilizar será https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Também pode utilizar o software iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.

### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações ocultas ou visíveis no mesmo formato.

### <a name="app-information-for-built-in-ios-apps"></a>Informações para aplicações iOS incorporadas
Utilize as informações nesta lista para identificar o nome, o publicador e o ID das aplicações iOS incorporadas que pretenda mostrar ou ocultar. Se pretender mostrar ou ocultar todas as aplicações na lista, pode copiar os dados abaixo para um ficheiro de texto com a extensão **.csv** e, em seguida, utilizar a opção **Importar** para importar todas as aplicações em simultâneo.


    App Store,Apple,com.apple.AppStore
    Calculator,Apple,com.apple.calculator
    Calendar,Apple,com.apple.mobilecal
    Camera,Apple,com.apple.camera
    Clock,Apple,com.apple.mobiletimer
    Compass,Apple,com.apple.compass
    Contacts,Apple,com.apple.MobileAddressBook
    FaceTime,Apple,com.apple.facetime
    Find Friends,Apple,com.apple.mobileme.fmf1
    Find iPhone,Apple,com.apple.mobileme.fmip1
    Game Center,Apple,com.apple.gamecenter
    GarageBand,Apple,com.apple.mobilegarageband
    Health,Apple,com.apple.Health
    iBooks,Apple,com.apple.iBooks
    iTunes Store,Apple,com.apple.MobileStore
    iTunes U,Apple,com.apple.itunesu
    Keynote,Apple,com.apple.Keynote
    Mail,Apple,com.apple.mobilemail
    Maps,Apple,com.apple.Maps
    Messages,Apple,com.apple.MobileSMS
    Music,Apple,com.apple.Music
    News,Apple,com.apple.news
    Notes,Apple,com.apple.mobilenotes
    Numbers,Apple,com.apple.Numbers
    Pages,Apple,com.apple.Pages
    Photo Booth,Apple,com.apple.Photo-Booth
    Photos,Apple,com.apple.mobileslideshow
    Podcasts,Apple,com.apple.podcasts
    Reminders,Apple,com.apple.reminders
    Safari,Apple,com.apple.mobilesafari
    Settings,Apple,com.apple.Preferences
    Stocks,Apple,com.apple.stocks
    Tips,Apple,com.apple.tips
    Videos,Apple,com.apple.videos
    VoiceMemos,Apple,com.apple.VoiceMemos
    Wallet,Apple,com.apple.Passbook
    Watch,Apple,com.apple.Bridge
    Weather,Apple,com.apple.weather





## <a name="cellular"></a>Rede móvel
-     **Roaming de dados** – Permita o roaming de dados quando o dispositivo estiver numa rede celular.
-     **Obtenção global em segundo plano em roaming** – Permita que o dispositivo obtenha dados, tais como e-mail, enquanto estiver em roaming numa rede celular.
-     **Marcação por voz** – Permita a utilização da funcionalidade de marcação por voz no dispositivo.
-     **Chamadas em roaming** – Permita chamadas em roaming quando o dispositivo estiver numa rede celular.
-     **Alterações às definições de utilização dos dados via rede móvel de aplicação (apenas supervisionado)** – Permita que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-     **Criar cópias de segurança na iCloud** – Permita ao utilizador criar uma cópia de segurança do dispositivo para iCloud.
-     **Sincronização de documentos com a iCloud (apenas supervisionado)** – Permita a sincronização de documentos e pares chave-valor para o seu espaço de armazenamento do iCloud.
-     **Sincronização de transmissão em fluxo de fotografias com a iCloud** – Permite aos utilizadores ativar **O Meu Fluxo de Fotografias** no dispositivo deles, o que permite que as fotografias sejam sincronizadas com o iCloud e disponibilizadas em todos os dispositivos dos utilizadores.
-     **Cópia de segurança encriptada** – Exija que qualquer cópia de segurança de um dispositivo seja encriptada.
-     **Fototeca em iCloud** – Se estiver definido como **Não**, desativará a utilização da biblioteca de fotografias do iCloud que permite aos utilizadores armazenar fotografias e vídeos na cloud.    Se isto estiver definido como **Não**, todas as fotografias que não tiverem sido completamente transferidas da Biblioteca de Fotografias do iCloud para o dispositivo serão removidas do mesmo.
-     **Sincronização das aplicações geridas com a cloud** – Permita que as aplicações que gere com o Intune sincronizem dados para a conta do iCloud dos utilizadores.
-     **Transmissão partilhada de fotografias** – Definido como **Não** para desativar a **Partilha de Fotografias do iCloud** no dispositivo.
-     **Continuação da atividade** – Permita ao utilizador continuar o trabalho que iniciou num dispositivo iOS noutro dispositivo iOS ou Mac OS X (Handoff).

## <a name="kiosk"></a>Kiosk
-     **Bloqueio de ativação** – Ative o Bloqueio de ativação em dispositivos iOS supervisionados.
-     **Aplicação que é executada no modo de local público** – Selecione **Aplicação Gerida** para selecionar uma aplicação que tenha adicionado ao Intune ou **Aplicação da Loja** para especificar o URL de uma aplicação na loja. Não será permitida a execução de outras aplicações no dispositivo. Para obter mais ajuda, consulte "Como especificar URLs para lojas de aplicações" mais adiante neste tópico.
-     **AssistiveTouch** – Ative ou desative a definição de acessibilidade **AssistiveTouch**, que ajuda o utilizador a executar gestos no ecrã que lhes poderão ser difíceis de realizar.
-     **Inverter cores** – Ative ou desative a definição de acessibilidade Inverter Cores, que ajusta o ecrã para ajudar utilizadores com deficiências visuais.
-     **Áudio mono** – Ative ou desative a definição de acessibilidade Áudio mono.
-     **VoiceOver** – Ative ou desative a definição de acessibilidade **VoiceOver**, que lê em voz alta o texto no ecrã do dispositivo.
-     **Zoom** – Ative ou desative a definição de acessibilidade **Zoom**, o que permite ao utilizador tocar para aplicar zoom no ecrã do dispositivo.
-     **Bloqueio automático** – Ative ou desative o bloqueio automático do dispositivo.
-     **Comutador do toque** – Ative ou desative a alteração do toque (desativar som) no dispositivo.
-     **Rotação do ecrã** – Ative ou desative a mudança da orientação do ecrã quando o utilizador rodar o dispositivo.
-     **Botão de suspensão do ecrã** – Ative ou desative o botão de reativação de suspensão do ecrã no dispositivo.
-     **Toque** – Ative ou desative o ecrã tátil do dispositivo.
-     **Botões de volume** – Ative ou desative a utilização dos botões de volume no dispositivo.
-     **Controlo do AssistiveTouch** – Ative ou desative os ajustes do AssistiveTouch, o que permite ao utilizador ajustar a função AssistiveTouch.
-     **Controlo de inversão de cores** – Ative ou desative a funcionalidade de inverter ajustes de cores, o que permite ao utilizador ajustar a função Inverter Cores.
-     **Falar em texto selecionado** – Ative ou desative as definições de acessibilidade Enunciar Seleção, que lê em voz alta o texto que o utilizador seleciona.
-     **Controlo de VoiceOver** – Ative ou desative os ajustes do VoiceOver, o que permite ao utilizador ajustar a função VoiceOver (por exemplo, a rapidez de leitura em voz alta do texto no ecrã).
-     **Controlo de zoom** – Ative ou desative os ajustes do zoom, o que permite ao utilizador ajustar a função zoom.

>[!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Para obter mais informações sobre a Ferramenta Apple Configurator, consulte a sua documentação da Apple.
>Se a aplicação iOS que especificou for instalada após a implementação da política de configuração, o dispositivo só entrará em modo de local público após ser reiniciado.

## <a name="safari"></a>Safari
-     **Safari (apenas supervisionado)** – Especifique se o browser Safari pode ser utilizado no dispositivo.
-     **Preenchimento automático** – Permita ao utilizador alterar as definições de conclusão automática no browser.
-     **Cookies** – Permita que o browser utilize cookies.
-     **JavaScript** – Permita a execução de scripts de Java no browser.
-     **Avisos de fraude** – Permita avisos de fraude no browser.
-     **Pop-ups** – Ative ou desative o bloqueador de janelas de pop-up do browser.

