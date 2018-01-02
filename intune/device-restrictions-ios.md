---
title: "Definições de restrição de dispositivos no Intune para dispositivos iOS"
titleSuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos iOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b871726c887916662986008010e0728811f2ba98
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/12/2017
---
# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos iOS no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Geral

-   **Submissão de dados de diagnóstico** – Permita ou impeça que o dispositivo submeta dados de diagnóstico à Apple.
-   **Captura de ecrã** – Permita ao utilizador capturar o conteúdo do ecrã como uma imagem.
    - **Observação remota do ecrã através da aplicação Classroom (apenas supervisionado)** – permita ou bloqueie a visualização do ecrã de dispositivos iOS por parte da aplicação Classroom da Apple.
    - **Observação não solicitada do ecrã através da aplicação Classroom (apenas supervisionado)** – se permitido, os professores podem observar o ecrã dos dispositivos iOS dos estudantes de forma silenciosa através da aplicação Classroom sem o conhecimento dos estudantes.
-   **Certificados TLS não fidedignos** – Permita certificados Transport Layer Security não fidedignos no dispositivo.
-   **Fidedignidade da aplicação empresarial** – Permite que o utilizador opte por confiar em aplicações que não foram transferidas a partir da loja de aplicações.
- **Modificação da conta (apenas supervisionado)** – quando está bloqueada, esta opção impede que o utilizador modifique as definições específicas do dispositivo a partir da aplicação de definições do iOS, como criar novas contas de dispositivo e alterar o nome de utilizador ou palavra-passe.
Também se aplica às definições acessíveis a partir da aplicação de definições do iOS, tais como o Correio, Contactos, Calendário, Facebook e Twitter. Não se aplica a aplicações com definições da conta que não sejam configuráveis a partir da aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.
- **Ativar restrições nas definições do dispositivo (apenas supervisionado)** – Permita que o utilizador configure as restrições de dispositivo (restrições de acesso) no dispositivo.
- **Utilização da opção Apagar todos os conteúdos e definições no dispositivo (apenas supervisionado)** – Permita que o utilizador utilize a opção de apagar todo o conteúdo e definições no dispositivo.
- **Modificação do nome do dispositivo (apenas supervisionado)** – Permita que o utilizador altere o nome do dispositivo.
- **Modificação das definições de notificação (apenas supervisionado)** – Permita que o utilizador altere as definições de notificação do dispositivo.
- **Modificação da imagem de fundo (apenas supervisionado)** – Permita que o utilizador altere a imagem de fundo do dispositivo.
- **Modificação das definições de fidedignidade de aplicações empresariais (apenas supervisionado)** – Permite que o utilizador opte por confiar em aplicações que não foram transferidas a partir da loja de aplicações.
- **Alterações do perfil de configuração (apenas supervisionado)** – Permita que o utilizador instale perfis de configuração.
- **Bloqueio de Ativação (apenas supervisionado)** – ative o Bloqueio de Ativação em dispositivos iOS supervisionados.

## <a name="configurations-requiring-supervision"></a>Configurações que necessitam de supervisão

O modo supervisionado do iOS só pode ser ativado durante a configuração inicial de dispositivos através do Programa de Registo de Aparelho da Apple ou com o Apple Configurator. Depois de ativar o modo supervisionado, o Intune pode configurar um dispositivo com a seguinte funcionalidade:

- Bloqueio de Aplicação (Modo de Aplicação Única) 
- Proxy HTTP Global 
- Ignorar Bloqueio de Ativação 
- Modo de Aplicação Única Autónomo 
- Filtro de Conteúdo Web 
- Definição de fundo e ecrã de bloqueio 
- Push da Aplicação Silencioso 
- VPN Sempre Ativada 
- Permitir exclusivamente a instalação de aplicações geridas 
- iBookstore 
- iMessages 
- Centro de Jogos 
- AirDrop 
- AirPlay 
- Emparelhamento de anfitrião 
- Sincronização de Nuvem 
- Pesquisa Spotlight 
- Handoff 
- Apagar dispositivo 
- Restrições da IU 
- Instalação dos perfis de configuração pela IU 
- Notícias 
- Atalhos de teclado 
- Modificações do código de acesso 
- Alterações do nome do dispositivo 
- Alterações da imagem de fundo 
- Transferências automáticas de aplicações 
- Alterações à confiança na aplicação de empresa 
- Apple Music 
- Mail Drop 
- Emparelhar com o Apple Watch 

> [!NOTE]
> A Apple confirmou que determinadas definições irão mudar para apenas supervisionado em 2018. Recomendamos que tenha isto em consideração ao utilizar estas definições em vez de aguardar que a Apple efetue a migração para apenas supervisionado:
> - Instalação da aplicação por utilizadores finais
> - Remoção de aplicações
> - FaceTime
> - Safari
> - iTunes
> - Conteúdos explícitos
> - Documentos e dados do iCloud
> - Jogos de vários jogadores
> - Adicionar amigos do Centro de Jogos

## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Palavras-passe simples** – Permita palavras-passe simples, como 0000 e 1234.
    -   **Tipo obrigatório de palavra-passe** – Especifique o tipo de palavra-passe que será obrigatório, como apenas numérica ou alfanumérica.
    -   **Número de carateres não-alfanuméricos na palavra-passe** – Especifique o número de carateres de símbolos (como **#** ou **@**) que tem de ser incluído na palavra-passe.
    -   **Comprimento mínimo da palavra-passe** – Especifique o número mínimo de carateres na palavra-passe.
    -   **Número de falhas de início de sessão antes de limpar o dispositivo** – Especifique o número de tentativas de início de sessão falhadas antes desta definição eliminar os dados do dispositivo.
    -   **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**<sup>1</sup> – Especifique durante quanto tempo o dispositivo pode permanecer inativo antes de o utilizador ter de reintroduzir a palavra-passe.
    -   **Máximo de minutos de inatividade até o ecrã ser bloqueado**<sup>1</sup> – Especifique o número de minutos antes de o ecrã do dispositivo se desligar.
    -   **Expiração de palavra-passe (dias)** – Especifique o número de dias antes de ser preciso alterar a palavra-passe do dispositivo.
    -   **Impedir a reutilização de palavras-passe anteriores** – Especifique o número de palavras-passe utilizadas anteriormente que o dispositivo possa ter memorizado.
    -   **Desbloqueio por impressão digital** – Permita a utilização de uma impressão digital para desbloquear dispositivos compatíveis.
- **Modificação do código de acesso (apenas supervisionado)** – impede que o código de acesso seja alterado, adicionado ou removido.
    - **Modificação de impressão digital (apenas supervisionado)** – impede o utilizador de alterar, adicionar ou remover as definições do Touch ID.

<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

-   **Acesso ao Centro de Controlo enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda ao centro de controlo quando o dispositivo está bloqueado.
-   **Notificações enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda à vista de notificações sem desbloquear o dispositivo.
-   **Passbook enquanto o dispositivo está bloqueado** – Permita que o utilizador aceda à aplicação Passbook enquanto o dispositivo está bloqueado.
-   **Vista Hoje enquanto o dispositivo está bloqueado** – Permita que o utilizador veja a vista Hoje enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos


-   **App Store** – bloqueie o acesso à loja de aplicações em dispositivos supervisionados.
    - **Instalar aplicações a partir da App Store (apenas supervisionado)** – bloqueia a loja de aplicações a partir do ecrã principal do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações.
    - **Transferências automáticas de aplicações (apenas supervisionado)** – impede que as aplicações que foram adquiridas noutro dispositivo iOS sejam transferidas para este dispositivo.
-   **Palavra-passe para aceder à loja de aplicações** – Exija ao utilizador que introduza uma palavra-passe antes de poder visitar a loja de aplicações.
-   **Compras via aplicação** – Permita que se façam compras na loja a partir de uma aplicação em execução.
-   **Conteúdo de música, podcast ou notícias explícito do iTunes (apenas supervisionado)** – Permita que o dispositivo aceda ao conteúdo classificado como para adultos a partir da loja.
-   **Transferir conteúdos da iBook store identificados como “Erótico”** – Permita que o utilizador transfira livros com a categoria “Erótico”.
-   **Ver documentos empresariais em aplicações não geridas** – Permita que os documentos empresariais sejam vistos em qualquer aplicação.<br>**Exemplo:** pretende impedir que os utilizadores guardem os ficheiros da aplicação OneDrive para a Dropbox. Configure esta definição como não. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não será permitido guardar.
-   **Ver documentos não empresariais em aplicações empresariais** – Permita que qualquer documento seja visto em aplicações empresariais geridas.
-   **Tratar o AirDrop como um destino não gerido** – Impede que as aplicações geridas possam enviar dados através do Airdrop.
-   **Adicionar amigos do Centro de Jogos (apenas supervisionado)** – Permita que o utilizador adicione amigos no Centro de Jogos.
-   **Centro de Jogos (apenas supervisionado)** – Bloqueie ou ative a utilização da aplicação do Centro de Jogos.
-   **Jogos de multijogadores (apenas supervisionado)** – Permita que o utilizador jogue jogos de multijogadores no dispositivo.
-   **Região das classificações** – Selecione a região das classificações para a qual quer configurar transferências permitidas e, em seguida, escolha as classificações permitidas para **Filmes** e **Programas de TV**.
-   **Aplicações** – Selecione a classificação etária permitida das aplicações que os utilizadores poderão transferir ou pode escolher **Permitir Todas as Aplicações**.

## <a name="built-in-apps"></a>Aplicações Incorporadas

-   **Câmara** – Selecione se a câmara do dispositivo pode ser utilizada.
    -   **FaceTime** – Permita que a aplicação FaceTime seja utilizada no dispositivo.
-   **Siri** – Permita a utilização do assistente de voz Siri no dispositivo.
    -   **Siri enquanto o dispositivo está bloqueado** – Permita a utilização do assistente de voz Siri no dispositivo enquanto está bloqueado.
    -   **Filtro de linguagem inapropriada da Siri (apenas supervisionado)** – Impede que a Siri dite ou fale com linguagem inapropriada.
    -   **A Siri pode consultar conteúdos gerados pelo utilizador a partir da Internet (apenas supervisionado)** – Permita que a Siri aceda a sites para responder a perguntas.
- **Apple News (apenas supervisionado)** – Permita a utilização da aplicação Apple News.
- **Loja iBooks (apenas supervisionado)** – Permita que o utilizador procure e compre livros da loja iBooks.
- **Aplicação Mensagens no dispositivo (apenas supervisionado)** – Permita a utilização da aplicação Mensagens para enviar e ler mensagens SMS.
- **Podcasts (apenas supervisionado)** – Permita a utilização da aplicação Podcasts.
- **Serviço Music (apenas supervisionado)** – Permita a utilização da aplicação Apple Music.
- **Serviço iTunes Radio (apenas supervisionado)** – Permita a utilização da aplicação iTunes Radio.
- **Alterações às definições da aplicação Encontrar Amigos (apenas supervisionado)** – Permita que o utilizador altere as definições da aplicação Encontrar Amigos.
- **A pesquisa Spotlight pode devolver resultados da Internet (apenas supervisionado)** – Permita que a pesquisa Spotlight se ligue à Internet para proporcionar mais resultados.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- Uma lista de **Aplicações proibidas** – Indique as aplicações (não geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar. Os utilizadores não são impedidos de instalar uma aplicação proibida mas, se o fizerem, isso ser-lhe-á comunicado.
- Uma lista de **Aplicações aprovadas** – Indique as aplicações que os utilizadores têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar aplicações que não se encontrem na lista aprovada, mas se o fizerem, esta ação ser-lhe-á comunicada.

Para configurar a lista, clique em **Adicionar** e, em seguida, especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Como especificar o URL para uma aplicação na loja

Para especificar um URL de aplicação na lista de aplicações, utilize o seguinte formato:

Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.
Copie o URL da página e utilize-o como o URL para configurar a lista das aplicações permitidas ou proibidas ou uma aplicação que pretende executar no modo de local público.
Os perfis de dispositivo que contêm as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

Exemplo: procure Microsoft Word para iPad. O URL que irá utilizar será https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.

### <a name="additional-options"></a>Opções adicionais

Também pode clicar em **Importar** para preencher a lista a partir de um ficheiro csv, no formato <*url da aplicação*>, <*nome da aplicação*>, <*publicador da aplicação*> ou clicar em **Exportar** para criar um ficheiro csv que contenha o conteúdo da lista de aplicações restritas no mesmo formato.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar ou ocultar aplicações (apenas supervisionado)

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


## <a name="wireless"></a>Sem fios
-   **Roaming de dados** – Permita o roaming de dados quando o dispositivo estiver numa rede celular.
-   **Obtenção global em segundo plano em roaming** – Permita que o dispositivo obtenha dados, tais como e-mail, enquanto estiver em roaming numa rede celular.
-   **Marcação por voz** – Permita a utilização da funcionalidade de marcação por voz no dispositivo.
-   **Chamadas em roaming** – Permita chamadas em roaming quando o dispositivo estiver numa rede celular.
-   **Alterações às definições de utilização dos dados via rede móvel de aplicação (apenas supervisionado)** – Permita que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.
-   **Hotspot Pessoal** – não permita que o dispositivo seja utilizado como um hotspot pessoal. Esta definição poderá não ser compatível com algumas operadoras.
-   **Adira a redes Wi-Fi apenas com perfis de configuração (apenas supervisionado)** – permita que o dispositivo se ligue apenas a redes Wi-Fi configuradas com um perfil Wi-Fi do Intune.

- **Regras de utilização de rede móvel (apenas aplicações geridas)** – permite-lhe definir os tipos de dados que as aplicações geridas podem utilizar em redes móveis. Escolha entre:
    - **Bloquear a utilização de dados via rede móvel**
    - **Bloquear a utilização de dados via rede móvel ao efetuar o roaming**

## <a name="connected-devices"></a>Dispositivos Ligados

-   **AirDrop (apenas supervisionado)** – Permitir a utilização da funcionalidade AirDrop para trocar conteúdos com dispositivos que se encontrem próximos.
-   **Emparelhamento com Apple Watch (apenas supervisionado)** – Permita que o dispositivo se emparelhe com um Apple Watch.
-   **Deteção de pulso para Apple Watch emparelhado** – Quando ativada, o Apple Watch não apresenta notificações quando não estiver a ser utilizado.
-   **Modificação de Bluetooth (apenas supervisionado)** – Não permita que o utilizador final altere as definições de Bluetooth no dispositivo.
-   **Emparelhamento de anfitriões para controlar os dispositivos com que um dispositivo iOS se pode emparelhar (apenas supervisionado)** – Permita o emparelhamento de anfitriões para permitir que o administrador tenha controlo sobre os dispositivos com os quais um dispositivo iOS pode ser emparelhado.
-   **Pedir palavra-passe de emparelhamento para pedidos do AirPlay a enviar** – Exija uma palavra-passe de emparelhamento quando o utilizador utiliza o AirPlay para a transmissão de conteúdo para outros dispositivos da Apple.

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

-   **Pesquisa de definição de palavras (apenas supervisionado)** – Permita a funcionalidade do iOS que permite realçar uma palavra e procurar a definição dela.
-   **Teclados preditivos (apenas supervisionado)** – Permita a utilização de teclados preditivos que sugerem palavras que o utilizador poderá querer utilizar.
-   **Correção automática (apenas supervisionado)** – Permite que o dispositivo corrija automaticamente palavras com erros ortográficos.
-   **Verificação ortográfica do teclado (apenas supervisionado)** – Permite o corretor ortográfico do dispositivo.
-   **Atalhos de teclado (apenas supervisionado)** – Permite a utilização de atalhos de teclado.
-   **Ditado (apenas supervisionado)** – impede o utilizador de utilizar entradas de voz para introduzir texto.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-   **Criar cópias de segurança na iCloud** – Permita ao utilizador criar uma cópia de segurança do dispositivo para iCloud.
-   **Sincronização de documentos com a iCloud (apenas supervisionado)** – Permita a sincronização de documentos e pares chave-valor para o seu espaço de armazenamento do iCloud.
-   **Sincronização de transmissão em fluxo de fotografias com a iCloud** – Permite aos utilizadores ativar **O Meu Fluxo de Fotografias** no dispositivo deles, o que permite que as fotografias sejam sincronizadas com o iCloud e disponibilizadas em todos os dispositivos dos utilizadores.
-   **Cópia de segurança encriptada** – Exija que qualquer cópia de segurança de um dispositivo seja encriptada.
-   **Fototeca em iCloud** – Se estiver definido como **Não**, desativará a utilização da biblioteca de fotografias do iCloud que permite aos utilizadores armazenar fotografias e vídeos na cloud.    Se isto estiver definido como **Não**, todas as fotografias que não tiverem sido completamente transferidas da Biblioteca de Fotografias do iCloud para o dispositivo serão removidas do mesmo.
-   **Sincronização das aplicações geridas com a cloud** – Permita que as aplicações que gere com o Intune sincronizem dados para a conta do iCloud dos utilizadores.
-   **Transmissão partilhada de fotografias** – Definido como **Não** para desativar a **Partilha de Fotografias do iCloud** no dispositivo.
-   **Continuação da atividade** – permita ao utilizador continuar o trabalho que iniciou num dispositivo iOS noutro dispositivo iOS ou macOS (Handoff).

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicação única autónomo (apenas supervisionado)

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado para que possa apenas executar essa aplicação. Um exemplo desta funcionalidade é quando configura uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="settings"></a>Definições

- **Nome da aplicação** –introduza o nome da aplicação conforme irá aparecer na lista de aplicações neste painel.
- **ID do Pacote de Aplicações** -introduza o ID do pacote da aplicação. Para obter ajuda, veja **Referência de ID do pacote para aplicações iOS incorporadas** deste tópico.

Depois de especificar cada nome da aplicação e ID do pacote, escolha **Adicionar** para o acrescentar à lista.

- **Importar** – importe um ficheiro de valores separados por vírgulas (.csv) que contenha uma lista de nomes das aplicações e os IDs de pacotes associados.
- **Exportar** – exporte os nomes das aplicações e IDs de pacotes associados que configurou para um ficheiro de valores separados por vírgulas (.csv).

### <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referência de ID do pacote para aplicações iOS incorporadas

Esta lista mostra o ID do pacote de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple


```


## <a name="kiosk-supervised-only"></a>Quiosque (apenas supervisionado)
-   **Aplicação que é executada no modo de local público** – Selecione **Aplicação Gerida** para selecionar uma aplicação que tenha adicionado ao Intune ou **Aplicação da Loja** para especificar o URL de uma aplicação na loja. Não será permitida a execução de outras aplicações no dispositivo. Para obter mais ajuda, consulte "Como especificar URLs para lojas de aplicações" mais adiante neste tópico.
    -   **AssistiveTouch** – Ative ou desative a definição de acessibilidade **AssistiveTouch**, que ajuda o utilizador a executar gestos no ecrã que lhes poderão ser difíceis de realizar.
    -   **Inverter cores** – Ative ou desative a definição de acessibilidade Inverter Cores, que ajusta o ecrã para ajudar utilizadores com deficiências visuais.
    -   **Áudio mono** – Ative ou desative a definição de acessibilidade Áudio mono.
    -   **VoiceOver** – Ative ou desative a definição de acessibilidade **VoiceOver**, que lê em voz alta o texto no ecrã do dispositivo.
    -   **Zoom** – Ative ou desative a definição de acessibilidade **Zoom**, o que permite ao utilizador tocar para aplicar zoom no ecrã do dispositivo.
    -   **Bloqueio automático** – Ative ou desative o bloqueio automático do dispositivo.
    -   **Comutador do toque** – Ative ou desative a alteração do toque (desativar som) no dispositivo.
    -   **Rotação do ecrã** – Ative ou desative a mudança da orientação do ecrã quando o utilizador rodar o dispositivo.
    -   **Botão de suspensão do ecrã** – Ative ou desative o botão de reativação de suspensão do ecrã no dispositivo.
    -   **Toque** – Ative ou desative o ecrã tátil do dispositivo.
    -   **Botões de volume** – Ative ou desative a utilização dos botões de volume no dispositivo.
    -   **Controlo do AssistiveTouch** – Ative ou desative os ajustes do AssistiveTouch, o que permite ao utilizador ajustar a função AssistiveTouch.
    -   **Controlo de inversão de cores** – Ative ou desative a funcionalidade de inverter ajustes de cores, o que permite ao utilizador ajustar a função Inverter Cores.
    -   **Falar em texto selecionado** – Ative ou desative as definições de acessibilidade Enunciar Seleção, que lê em voz alta o texto que o utilizador seleciona.
    -   **Controlo de VoiceOver** – Ative ou desative os ajustes do VoiceOver, o que permite ao utilizador ajustar a função VoiceOver (por exemplo, a rapidez de leitura em voz alta do texto no ecrã).
    -   **Controlo de zoom** – Ative ou desative os ajustes do zoom, o que permite ao utilizador ajustar a função zoom.

>[!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Para obter mais informações sobre a Ferramenta Apple Configurator, consulte a sua documentação da Apple.
>Se a aplicação iOS que especificou for instalada após a atribuição do perfil, o dispositivo só entrará em modo de quiosque após ser reiniciado.

## <a name="safari"></a>Safari
-   **Safari (apenas supervisionado)** – Especifique se o browser Safari pode ser utilizado no dispositivo.
-   **Preenchimento automático** – Permita ao utilizador alterar as definições de conclusão automática no browser.
-   **Cookies** – Permita que o browser utilize cookies.
-   **JavaScript** – Permita a execução de scripts de Java no browser.
-   **Avisos de fraude** – Permita avisos de fraude no browser.
-   **Pop-ups** – Ative ou desative o bloqueador de janelas de pop-up do browser.


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Domínios de e-mail não marcados

No campo **URL de Domínio de E-mail**, adicione um ou mais URLs à lista. Quando os utilizadores finais recebem um e-mail de um domínio não configurado, o e-mail será marcado como não fidedigno na aplicação Correio do iOS.


### <a name="managed-web-domains"></a>Domínios Web geridos

No campo **URL de Domínio Web**, adicione um ou mais URLs à lista. Quando os documentos são transferidos a partir de domínios especificados, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.


### <a name="safari-password-autofill-domains"></a>Domínios de preenchimento automático de palavras-passe do Safari

No campo **URL de Domínio**, adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Esta definição aplica-se apenas ao browser Safari e aos dispositivos iOS 9.3 e posterior no modo supervisionado. Se não especificar nenhum URL, as palavras-passe poderão ser guardadas a partir de todos os sites.
