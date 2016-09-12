---
title: "Definições de política do iOS | Microsoft Intune"
description: "Crie políticas que controlam as definições e funcionalidades em dispositivos iOS que gere com o Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 65d2c9c1f5d81dae33422bd4bf7c0e2e21bb96e4
ms.openlocfilehash: 13b8bd8c3269be60d66c4e79551f662205afcea0


---

# Definições de política do iOS no Microsoft Intune

O Intune oferece uma variedade de definições gerais incorporadas que pode configurar nos dispositivos iOs. Além disso, pode utilizar a ferramenta Apple Configurator para criar definições personalizadas que não estão disponíveis no Intune.

## Definições de política de configuração geral

Utilize a **política de configuração geral do iOS** do Microsoft Intune para configurar definições para:

-   **Dispositivo geral, e definições de segurança**. Escolha entre uma lista de predefinições que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Modo de local público**. Bloqueie um dispositivo para que apenas algumas funcionalidades possam ser utilizadas. Por exemplo, pode permitir que um dispositivo execute apenas uma aplicação gerida que especificar ou pode desativar os botões de volume num dispositivo. Estas definições podem ser utilizadas para um modelo de demonstração de um dispositivo ou para um dispositivo com a finalidade de desempenhar apenas uma função, como um dispositivo de ponto de venda.

-   **Aplicações compatíveis e incompatíveis**. Especifique uma lista de aplicações que são compatíveis ou incompatíveis com a sua empresa. Em dispositivos Android e iOS, o **Relatório de Aplicações Não Compatíveis** pode ser utilizado para ver a compatibilidade de aplicações que especificou na lista comparativamente às aplicações instaladas pelos utilizadores (mas não pode bloquear a instalação da aplicação).

> [!TIP]
> Pode configurar termos e condições para os utilizadores para garantir que estes têm conhecimento de que as aplicações nos respetivos dispositivos (incluindo aplicações pessoais) serão avaliadas e que as aplicações não compatíveis serão bloqueadas ou comunicadas como não compatíveis. Os utilizadores têm de aceitar estes termos e condições antes de poderem inscrever os respetivos dispositivos e utilizar o portal da empresa para obter aplicações. Para obter mais informações sobre como utilizar os termos e condições, consulte [Definições de políticas de termos e condições no Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se a definição que procura não aparecer neste tópico, poderá conseguir criá-la utilizando uma política personalizada de iOS que permita importar as definições que criou utilizando a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para mais informações, consulte "Definições de política personalizada" mais adiante neste tópico.

### Definições de segurança
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Especifique se o utilizador é obrigado a introduzir uma palavra-passe para aceder ao respetivo dispositivo.|
|**Tipo obrigatório de palavra-passe**|Especifique o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|
|**Número de carateres complexos necessários na palavra-passe**|Especifique o número de caracteres de símbolos (como **#** ou **@**) que têm de ser incluídos na palavra-passe.|
|**Comprimento mínimo da palavra-passe**|Especifique o número mínimo de carateres na palavra-passe.|
|**Permitir palavras-passe simples**|Permite palavras-passe simples, como **0000** e **1234**.|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Especifique o número de tentativas de início de sessão falhadas antes desta definição apaga o dispositivo.|
|**Minutos de inatividade antes de ser exigida a palavra-passe**<sup>1</sup>|Especifique o período de tempo durante o qual o dispositivo pode permanecer inativo antes de o utilizador ter de reintroduzir a palavra-passe.|
|**Expiração da palavra-passe (dias)**|Especifique o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|
|**Memorizar histórico de palavras-passe**|Especifique se o utilizador pode utilizar palavras-passe que utilizou anteriormente.|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifique o número de palavras-passe utilizadas anteriormente que o dispositivo memorizou.|
|**Minutos de inatividade antes de o ecrã se desligar**<sup>1</sup>|Especifique o número de minutos antes de o ecrã do dispositivo se desligar.|
|**Permitir desbloqueio por impressão digital**|Permite a utilização de uma impressão digital para desbloquear o dispositivo.|
<sup>1</sup> Para dispositivos iOS, quando configura as definições **Minutos de inatividade antes de o ecrã se desligar** e **Minutos de inatividade antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

### Definições do sistema
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir captura de ecrã**|Permitir ao utilizador capturar o conteúdo do ecrã como uma imagem.|
|**Permitir centro de controlo no ecrã de bloqueio**|Permitir que o utilizador aceda ao centro de controlo quando o dispositivo está bloqueado.|
|**Permitir vista de notificações no ecrã de bloqueio**|Permite que o utilizador aceda à vista de notificações sem desbloquear o dispositivo.|
|**Permitir vista atual no ecrã de bloqueio**|Permitir que o utilizador veja as notificações quando o dispositivo está bloqueado.|
|**Permitir certificados TLS não fidedignos**|Permitir certificados Transport Layer Security não fidedignos no dispositivo.|
|**Permitir submissão de dados de diagnóstico**|Permitir ou impedir o dispositivo de submeter dados de diagnóstico para a Apple.|
|**Permitir passbook quando bloqueado**|Permitir que o utilizador aceda à aplicação Passbook quando o dispositivo está bloqueado.|

### Definições da nuvem para documentos e dados
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir cópia de segurança para iCloud**|Permitir ao utilizador realizar uma cópia de segurança do dispositivo para iCloud.|
|**Permitir sincronização de documentos para iCloud**|Permitir a sincronização de documentos e pares chave-valor para o seu espaço de armazenamento do iCloud.|
|**Permitir sincronização de Fluxo de Fotografias para iCloud**|Permitir a sincronização das fotografias no dispositivo com o iCloud.|
|**Exigir cópia de segurança encriptada**|Exigir que qualquer cópia de segurança seja encriptada.|
|**Permitir que as aplicações geridas sincronizem dados para o serviço iCloud**|Permitir que as aplicações que gere com o Intune sincronizem dados para a conta do iCloud dos utilizadores.|
|**Permitir que o Handoff continue as atividades noutro dispositivo**|Permitir ao utilizador continuar o trabalho que iniciaram num dispositivo iOS noutro dispositivo iOS ou Mac OS X.|

### Definições da aplicação para o browser
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir o Safari**|Especificar se o browser Safari pode ser utilizado no dispositivo.|
|**Permitir preenchimento automático**|Permitir ao utilizador alterar as definições de conclusão automática no browser.|
|**Permitir bloqueador de janelas de pop-up**|Ativar ou desativar o bloqueador de janelas de pop-up do browser.|
|**Permitir cookies**|Permitir que o browser utilize cookies.|
|**Permitir scripting de Java**|Permitir a execução de scripts de Java no browser.|
|**Permitir aviso de fraude**|Permitir avisos de fraude no browser.|

### Definições da aplicação para aplicações
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir loja de aplicações**|Permitir que o dispositivo aceda à loja de aplicações.|
|**Exigir uma palavra-passe para aceder à loja de aplicações**|Exigir ao utilizador que introduza uma palavra-passe antes de poderem visitar a loja de aplicações.|
|**Permitir compras via aplicação**|Permite efetuar compras na loja a partir de uma aplicação em execução.|
|**Permitir documentos geridos em outras aplicações não geridas**|Permitir que documentos corporativos sejam exibidos em qualquer aplicação.<br>**Exemplo:** pretende impedir que os utilizadores guardem os ficheiros da aplicação OneDrive para a Dropbox. Configure esta definição como não. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não será permitido guardar.|
|**Permitir documentos não geridos em outras aplicações geridas**|Permitir a visualização de qualquer documento em aplicações geridas empresariais.|
|**Permitir videoconferência**|Permitir aplicações de videoconferência, tais como FaceTime, no dispositivo.|
|**Permitir conteúdo para adultos no arquivo de multimédia**|Permitir que o dispositivo aceda a conteúdo da loja classificado como conteúdo para adultos.|
|**Permitir que o utilizador transfira conteúdos da loja iBook sinalizado como "Erótico"**|Permitir ao utilizador transferir livros da categoria "Erótico".|

### Definições da aplicação para jogos
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a adição de amigos do Centro de Jogos**|Permitir que o utilizador adicione amigos no Centro de jogos.|
|**Permitir jogos multijogador**|Permitir que o utilizador jogue jogos multijogador no dispositivo.|

### Definições das capacidades do dispositivo para hardware
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir câmara**|Especifique se a câmara do dispositivo pode ser utilizada.|
|**Requerer palavra-passe emparelhada para os pedidos AirPlay enviados**|Exigir uma palavra-passe de emparelhamento quando o utilizador utiliza AirPlay para conteúdo de fluxo com outros dispositivos da Apple.|

### Definições das capacidades do dispositivo para a rede móvel
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir chamadas em roaming**|Permitir chamadas em roaming quando o dispositivo estiver numa rede celular.|
|**Permitir roaming de dados**|Permite o roaming de dados quando o dispositivo estiver numa rede celular.|
|**Permitir obtenção global em segundo plano em roaming**|Permitir que o dispositivo obtenha dados, tais como e-mail, enquanto estiver em roaming numa rede celular.|

### Definições das capacidades do dispositivo para funcionalidades
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a Siri**|Permitir a utilização do assistente de voz Siri no dispositivo.|
|**Permitir a Siri quando o dispositivo está bloqueado**|Permitir a utilização do assistente de voz Siri no dispositivo enquanto está bloqueado.|
|**Permitir marcação por voz**|Permitir a utilização da funcionalidade de marcação por voz no dispositivo.|


### Definições para aplicações conformes e não conformes
Na lista **Aplicações Conformes &amp;Não Conformes**, especifique uma lista de aplicações conformes ou não conformes utilizando as informações seguintes.

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações conformes ou uma lista de aplicações não conformes. Não é possível especificar ambas na mesma política.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indique as aplicações (não são geridas pelo Intune) que os utilizadores não têm permissão para instalar e executar.|
|**Comunicar não conformidade quando os utilizadores instalam aplicações não listadas**|Indique as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.|
|**Adicionar**|Adicionar uma aplicação à lista selecionada. Especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações. Ler "Como especificar URLs para lojas de aplicações" mais adiante neste tópico para obter ajuda.|
|**Importar Aplicações**|Importe uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. No ficheiro, utilize este formato: nome da aplicação, fabricante e URL da aplicação.|
|**Editar**|Editar nome, fabricante e URL da aplicação selecionada.|
|**Eliminar**|Eliminar a aplicação selecionada da lista.|

### Definições do modo de local público

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Selecione uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público**|Escolher **Procurar**e, em seguida, especifique a aplicação gerida ou a aplicação de uma loja que terá permissão para ser executada quando o dispositivo estiver em modo de local público. Não será permitida a execução de outras aplicações no dispositivo. Para obter mais ajuda, consulte "Como especificar URLs para lojas de aplicações" mais adiante neste tópico.|
|**Permitir toque**|Ativar ou desativar o ecrã tátil do dispositivo.|
|**Permitir a rotação do ecrã**|Ativar ou desativar a mudança da orientação do ecrã quando o utilizador rodar o dispositivo.|
|**Permitir os botões de volume**|Ativar ou desativar a utilização dos botões de volume no dispositivo.|
|**Permitir a alteração do toque**|Ativar ou desativar a alteração do toque (sem som) no dispositivo.|
|**Permitir o botão suspender/reativar ecrã**|Ativar ou desativar o botão de reativação de suspensão do ecrã no dispositivo.|
|**Permitir o bloqueio automático**|Ativar ou desativar o bloqueio automático do dispositivo.|
|**Ativar o áudio mono**|Ativar ou desativar a definição de acessibilidade **Áudio Mono**.|
|**Ativar o VoiceOver**|Ativar ou desativar a definição de acessibilidade **VoiceOver**, que lê em voz alta o texto no ecrã do dispositivo.|
|**Ativar ajustes do VoiceOver**|Ativar ou desativar os ajustes do VoiceOver, o que permite ao utilizador ajustar a função VoiceOver (por exemplo, a rapidez de leitura em voz alta do texto no ecrã).|
|**Ativar o Zoom**|Ativar ou desativar a definição de acessibilidade **Zoom** , o que permite ao utilizador tocar para aplicar zoom no ecrã do dispositivo.|
|**Ativar os ajustes do Zoom**|Ativar ou desativar os ajustes do Zoom, o que permite ao utilizador ajustar a função Zoom.|
|**Ativar a funcionalidade Inverter Cores**|Ativar ou desativar a definição de acessibilidade **Inverter cores**, que ajusta o ecrã para ajudar os utilizadores com deficiências visuais.|
|**Ativar os ajustes da funcionalidade Inverter Cores**|Ativar ou desativar a funcionalidade de inverter ajustes de cores, o que permite ao utilizador ajustar a função Inverter Cores.|
|**Ativar o AssistiveTouch**|Ativar ou desativar a definição de acessibilidade **AssistiveTouch** , que ajuda o utilizador a executar gestos no ecrã que lhes poderão ser difíceis de efetuar.|
|**Ativar os ajustes do AssistiveTouch**|Ativar ou desativar os ajustes do AssistiveTouch, o que permite ao utilizador ajustar a função AssistiveTouch.|
|**Ativar a funcionalidade Enunciar seleção**|Ativar ou desativar a definição de acessibilidade **Enunciar Seleção** , que lê em voz alta o texto que o utilizador seleciona.|
> [!NOTE]
> As seguintes notas aplicam-se às definições do modo de local público para dispositivos iOS:
>
> -   Antes de poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) ou o gestor de inscrição de dispositivos para colocar o dispositivo em modo supervisionado. Para obter mais informações sobre a Ferramenta Apple Configurator, consulte a sua documentação da Apple.
> -   Se a aplicação iOS que especificou for instalada após a implementação da política de configuração, o dispositivo só entrará em modo de local público após ser reiniciado.

### Informações de referência para aplicações conformes e não conformes

Utilize o **Relatório de Aplicações Não Conformes** para ver a conformidade das aplicações permitidas e bloqueadas.

##### Para executar o Relatório de Aplicações Não Conformes

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Relatórios** &gt; **Relatório de Aplicações Não Conformes**.

2.  Selecione os grupos de dispositivos que pretende verificar, selecione se pretende verificar as aplicações compatíveis, as aplicações não compatíveis ou ambas e, em seguida, selecione **Ver Relatório**.

#### Como especificar URLs para lojas de aplicações
Para especificar o URL de uma aplicação na lista de aplicações compatíveis e não compatíveis ou na opção **Selecionar uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público** (apenas em iOS), utilize o seguinte formato:

1. Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.

2. Copie o URL da página e utilize-o como o URL para configurar a lista das aplicações compatíveis ou não compatíveis que pretende executar no modo de local público.

**Exemplo:** Procure por **Microsoft Word para iPad**. O URL que irá utilizar será **https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Também pode utilizar o software iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.

### Definições de inscrição
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir Bloqueio de Ativação quando o dispositivo estiver no modo supervisionado**|Ativar o Bloqueio de Ativação em dispositivos iOS supervisionados.|

### Supervisão
Pode configurar as seguintes definições em dispositivos com iOS 7.1 e posterior que estejam no modo supervisionado.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir modificação da conta**|Permitir que o utilizador alterar as definições de conta, tais como configurações de e-mail.|
|**Permitir AirDrop**|Permitir a utilização da funcionalidade AirDrop para trocar conteúdos com dispositivos que se encontrem próximos.|
|**Permitir alterações às definições de utilização de dados via rede móvel da aplicação**|Permitir que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.|
|**Permitir que a Siri consulte conteúdos gerados pelo utilizador a partir da Internet**|Permitir que a Siri aceda a sites para responder a perguntas.|
|**Permitir acesso à loja iBooks**|Permitir que o utilizador procure e compre livros da loja iBooks.|
|**Permitir alterações para as definições da aplicação Encontrar Amigos**|Permitir que o utilizador altere as definições da aplicação Encontrar Amigos.|
|**Permitir a utilização das opções apagar todos os conteúdos e definições do dispositivo**|Permitir que o utilizador utilize a opção de apagar todos os conteúdos e definições do dispositivo.|
|**Permitir que o utilizador ative restrições nas definições do dispositivo**|Permitir que o utilizador configure as restrições de dispositivo (restrições de acesso) no dispositivo.|
|**Permitir a pesquisa Spotlight para devolver resultados da Internet**|Permitir a ligação da pesquisa Spotlight à Internet para fornecer mais resultados.|
|**Permitir a utilização da aplicação Game Center**|Permitir utilização da aplicação Game Center.|
|**Permitir emparelhamento de anfitrião para controlar os dispositivos aos quais um dispositivo iOS pode estar emparelhado**|Permitir o emparelhamento de anfitrião para permitir ao administrador o controlo sobre que dispositivos um dispositivo iOS 7 pode ser emparelhado com.|
|**Permitir que o utilizador instale perfis e certificados de configuração**|Permitir que o utilizador instale perfis e certificados de configuração.|
|**Permitir a utilização da aplicação Mensagens no dispositivo**|Permitir a utilização da aplicação Mensagens para enviar mensagens de texto.|

### Mostrar ou Ocultar Aplicações

Utilize a **Lista de aplicações ocultas e apresentadas** para controlar o seguinte nos dispositivos supervisionados com o iOS 9.3 ou posterior:

- Especificar uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
- Especificar uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.


#### Como criar uma lista de aplicações ocultas ou apresentadas

Especifique as seguintes definições:

|Nome da definição|Detalhes|
|-|-|
|**Lista de aplicações ocultas e apresentadas**|Ative esta definição se pretender criar uma lista de aplicações ocultas ou apresentadas.|
|**Ocultar dos utilizadores as aplicações listadas**|Selecione esta opção se pretender criar uma lista de aplicações que serão ocultadas dos utilizadores.|
|**Mostrar aos utilizadores apenas as aplicações listadas**|Selecione esta opção se pretender criar uma lista de aplicações que serão apresentadas aos utilizadores.<br>Quando cria este tipo de lista, todas as outras aplicações, exceto para **Definições** e **Telefone** (para iPhones) do iOS, estão ocultadas.<br>Além disso, tem de adicionar o Portal da Empresa e todas as aplicações que tiver implementado e que gere com o Intune à lista.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada.<br>Em relação à lista oculta, tem de especificar o **Nome**, **Publicador** e **URL da Aplicação ou ID do Pacote** de cada aplicação que pretende ocultar.<br>Para obter a lista apresentada, pode **Selecionar uma aplicação gerida** que fornece uma lista das aplicações que gere com o Intune para seleção ou Selecionar uma aplicação de loja, tendo de especificar em seguida o **Nome**, **Publicador**e **URL da Aplicação ou ID do Pacote** de cada aplicação que pretende apresentar.|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|

#### Informações para aplicações iOS incorporadas

Utilize as informações nesta lista para identificar o nome, o publicador e o ID das aplicações iOS incorporadas que pretenda mostrar ou ocultar. Se pretender mostrar ou ocultar todas as aplicações na lista, pode copiar os dados abaixo para um ficheiro de texto com a extensão **.csv** e, em seguida, utilizar a opção **Importar Aplicações** para importar todas as aplicações em simultâneo.

```
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


```




## Definições de política personalizada

Utilizar a **política personalizada do iOs** do Itune da Microsoft para implementar as definições que criou utilizando a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) para dispositivos iOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para uma política personalizada do iOS do Intune e implementar as definições em utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe a implementação de definições do iOS que não são configuráveis com as políticas de configuração gerais do Intune.

### Pré-requisitos
Antes de começar, tem de ter instalado o Apple Configurator e criar um ficheiro de configuração que contém as definições que pretende implementar nos utilizadores ou dispositivos. Pode transferir e obter informações sobre o Apple Configurator na [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> O Intune não comunica a conformidade de definições individuais em políticas personalizadas do iOS. No entanto, a conformidade geral das políticas é comunicada.

### Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política personalizada do iOS para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política personalizada do iOS e outras informações relevantes que o ajudem a localizá-la.|

### Definições personalizadas

|Nome da definição|Detalhes|
    |----------------|--------------------|
|**Nome do perfil de configuração personalizado (apresentado aos utilizadores)**|Indique um nome para a política tal como será apresentado no dispositivo e nos relatórios de políticas do Intune.|
|**Ficheiro de perfil de configuração**|Escolha **Importar** e em seguida, navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator. **Nota:** Certifique-se de que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do iOS nos dispositivos nos quais implementou a política personalizada do iOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).|
    |**Detalhes do perfil de configuração**|Apresentar o código XML do perfil de configuração que importou.|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO3-->


