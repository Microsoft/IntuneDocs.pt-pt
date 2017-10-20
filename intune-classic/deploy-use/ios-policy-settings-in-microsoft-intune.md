---
title: "Definições de política para iOS"
description: "Crie políticas que controlam as definições e funcionalidades em dispositivos iOS que gere com o Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9a6792de4556cae9d6429efafa9e6a8351f5f5a6
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Definições de política do iOS no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O Intune oferece uma variedade de definições gerais incorporadas que pode configurar nos dispositivos iOS. Além disso, pode utilizar a ferramenta Apple Configurator para criar definições personalizadas que não estão disponíveis no Intune.

## <a name="general-configuration-policy-settings"></a>Definições de política de configuração geral

Utilize a **política de configuração geral do iOS** do Microsoft Intune para configurar definições para:

-   **Dispositivo geral e definições de segurança**. Escolha entre uma lista de predefinições que permitem controlar uma série de funcionalidades e a funcionalidade do dispositivo.

-   **Modo de local público**. Bloqueie um dispositivo para que apenas algumas funcionalidades possam ser utilizadas. Por exemplo, pode permitir que um dispositivo execute apenas uma aplicação gerida que especificar ou pode desativar os botões de volume num dispositivo. Estas definições podem ser utilizadas para um modelo de demonstração de um dispositivo ou para um dispositivo com a finalidade de desempenhar apenas uma função, como um dispositivo de ponto de venda.

-   **Aplicações compatíveis e incompatíveis**. Especifique uma lista de aplicações que são compatíveis ou incompatíveis com a sua empresa. Em dispositivos Android e iOS, o **Relatório de Aplicações Não Compatíveis** pode ser utilizado para ver a compatibilidade de aplicações que especificou na lista comparativamente às aplicações instaladas pelos utilizadores (mas não pode bloquear a instalação da aplicação).

> [!TIP]
> Pode configurar termos e condições para os utilizadores para garantir que estes têm conhecimento de que as aplicações nos respetivos dispositivos (incluindo aplicações pessoais) serão avaliadas e que as aplicações não compatíveis serão bloqueadas ou comunicadas como não compatíveis. Os utilizadores têm de aceitar estes termos e condições antes de poderem inscrever os respetivos dispositivos e utilizar o portal da empresa para obter aplicações. Para obter mais informações sobre como utilizar os termos e condições, consulte [Definições de políticas de termos e condições no Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se a definição que procura não aparecer neste tópico, poderá conseguir criá-la utilizando uma política personalizada de iOS que permita importar as definições que criou utilizando a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para mais informações, consulte "Definições de política personalizada" mais adiante neste tópico.

### <a name="security-settings"></a>Definições de segurança
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Exigir uma palavra-passe para desbloquear os dispositivos móveis**|Especifique se o utilizador é obrigado a introduzir uma palavra-passe para aceder ao respetivo dispositivo.|
|**Tipo obrigatório de palavra-passe**|Especifique o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|
|**Número de carateres complexos obrigatórios na palavra-passe**|Especifique o número de caracteres de símbolos (como **#** ou **@**) que têm de ser incluídos na palavra-passe.|
|**Comprimento mínimo da palavra-passe**|Especifique o número mínimo de carateres na palavra-passe.|
|**Permitir palavras-passe simples**|Permite palavras-passe simples, como **0000** e **1234**.|
|**Número de falhas de início de sessão consecutivas a permitir antes de o dispositivo ser apagado**|Especifique o número de tentativas de início de sessão falhadas antes desta definição apaga o dispositivo.|
|**Minutos de inatividade antes de a palavra-passe ser exigida**<sup>1</sup>|Especifique o período de tempo durante o qual o dispositivo pode permanecer inativo antes de o utilizador ter de reintroduzir a palavra-passe.|
|**Expiração da Palavra-passe (dias)**|Especifique o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|
|**Memorizar histórico de palavras-passe**|Especifique se o utilizador pode utilizar palavras-passe que utilizou anteriormente.|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifique o número de palavras-passe utilizadas anteriormente que o dispositivo memorizou.|
|**Minutos de inatividade antes de o ecrã se desligar**<sup>1</sup>|Especifique o número de minutos antes de o ecrã do dispositivo se desligar.|
|**Permitir desbloqueio por impressão digital**|Permite a utilização de uma impressão digital para desbloquear o dispositivo.|
<sup>1</sup>Para dispositivos iOS, quando configura as definições **Minutos de inatividade antes de o ecrã se desligar** e **Minutos de inatividade antes de a palavra-passe ser exigida**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

### <a name="system-settings"></a>Definições do sistema
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir captura de ecrã**|Permitir ao utilizador capturar o conteúdo do ecrã como uma imagem.|
|**Permitir centro de controlo no ecrã de bloqueio**|Permitir que o utilizador aceda ao centro de controlo quando o dispositivo está bloqueado.|
|**Permitir vista de notificações no ecrã de bloqueio**|Permite que o utilizador aceda à vista de notificações sem desbloquear o dispositivo.|
|**Permitir vista atual no ecrã de bloqueio**|Permitir que o utilizador veja as notificações quando o dispositivo está bloqueado.|
|**Permitir certificados TLS não fidedignos**|Permitir certificados Transport Layer Security não fidedignos no dispositivo.|
|**Permitir submissão de dados de diagnóstico**|Permitir ou impedir o dispositivo de submeter dados de diagnóstico para a Apple.|
|**Permitir passbook quando bloqueado**|Permitir que o utilizador aceda à aplicação Passbook quando o dispositivo está bloqueado.|

### <a name="cloud-settings-for-documents-and-data"></a>Definições da cloud para documentos e dados
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir cópia de segurança para iCloud**|Permitir ao utilizador realizar uma cópia de segurança do dispositivo para iCloud.|
|**Permitir sincronização de documentos para iCloud**|Permitir a sincronização de documentos e pares chave-valor para o seu espaço de armazenamento do iCloud.|
|**Permitir sincronização de Fluxo de Fotografias para iCloud**|Permite aos utilizadores ativar **O Meu Fluxo de Fotografias** no respetivo dispositivo, o que permite que as fotografias sejam sincronizadas com o iCloud e disponibilizadas em todos os dispositivos dos utilizadores.|
|**Exigir cópia de segurança encriptada**|Exigir que qualquer cópia de segurança seja encriptada.|
|**Permitir que as aplicações geridas sincronizem dados para o serviço iCloud**|Permitir que as aplicações que gere com o Intune sincronizem dados para a conta do iCloud dos utilizadores.|
|**Permitir que o Handoff continue as atividades noutro dispositivo**|Permitir ao utilizador continuar o trabalho que iniciaram num dispositivo iOS noutro dispositivo iOS ou Mac OS X.|
|**Permitir Partilha de Fotografias em iCloud**|Definido como **Não** para desativar a **Partilha de Fotografias do iCloud** no dispositivo.|
|**Permitir Fototeca em iCloud**|Se estiver definido como **Não**, desativa a utilização da biblioteca de fotografias do iCloud que permite aos utilizadores armazenar fotografias e vídeos na cloud.   Se isto estiver definido como **Não**, todas as fotografias que não tiverem sido completamente transferidas da Biblioteca de Fotografias do iCloud para o dispositivo serão removidas do mesmo.|

### <a name="application-settings-for-the-browser"></a>Definições da aplicação para o browser
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir o Safari**|Especificar se o browser Safari pode ser utilizado no dispositivo.|
|**Permitir preenchimento automático**|Permitir ao utilizador alterar as definições de conclusão automática no browser.|
|**Permitir bloqueador de janelas pop-up**|Ativar ou desativar o bloqueador de janelas de pop-up do browser.|
|**Permitir cookies**|Permitir que o browser utilize cookies.|
|**Permitir scripting de Java**|Permitir a execução de scripts de Java no browser.|
|**Permitir aviso de fraude**|Permitir avisos de fraude no browser.|

### <a name="application-settings-for-apps"></a>Definições da aplicação para aplicações
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a instalação de aplicações**|Permitir que o dispositivo aceda à loja de aplicações e instale aplicações.|
|**Exigir uma palavra-passe para aceder à loja de aplicações**|Exigir ao utilizador que introduza uma palavra-passe antes de poderem visitar a loja de aplicações.|
|**Permitir compras via aplicação**|Permite efetuar compras na loja a partir de uma aplicação em execução.|
|**Permitir documentos geridos em outras aplicações não geridas**|Permitir que documentos corporativos sejam exibidos em qualquer aplicação.<br>**Exemplo:** pretende impedir que os utilizadores guardem os ficheiros da aplicação OneDrive para a Dropbox. Configure esta definição como não. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não será permitido guardar.|
|**Permitir documentos não geridos em outras aplicações geridas**|Permitir a visualização de qualquer documento em aplicações geridas empresariais.|
|**Permitir videoconferência**|Permitir aplicações de videoconferência, tais como FaceTime, no dispositivo.|
|**Permitir ao utilizador confiar em novos autores de aplicações empresariais**|Permite que o utilizador opte por confiar em aplicações que não foram transferidas a partir da loja de aplicações.|


### <a name="application-settings-for-games"></a>Definições da aplicação para jogos
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a adição de amigos do Centro de Jogos**|Permitir que o utilizador adicione amigos no Centro de jogos.|
|**Permitir jogos multijogador**|Permitir que o utilizador jogue jogos multijogador no dispositivo.|

### <a name="application-settings-for-media-content"></a>Definições da aplicação para conteúdo multimédia
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Região das classificações**|Selecione uma região e, em seguida, selecione a classificação máxima que os utilizadores podem transferir para **Filmes**, **Programas de TV** e **Aplicações**.|
|**Permitir conteúdo para adultos no arquivo de multimédia**|Permitir que o dispositivo aceda a conteúdo da loja classificado como conteúdo para adultos.|
|**Permitir que o utilizador transfira conteúdos da loja iBook sinalizados como “Erótico”**|Permitir ao utilizador transferir livros da categoria "Erótico".|


### <a name="device-capabilities-settings-for-hardware"></a>Definições das capacidades do dispositivo para hardware
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir câmara**|Especifique se a câmara do dispositivo pode ser utilizada.|
|**Forçar os Relógios Apple emparelhados a utilizar deteção no pulso**|Quando ativada, o Apple Watch não apresenta notificações quando não estiver a ser utilizado.|
|**Exigir palavra-passe emparelhada para os pedidos AirPlay enviados**|Exigir uma palavra-passe de emparelhamento quando o utilizador utiliza AirPlay para conteúdo de fluxo com outros dispositivos da Apple.|

### <a name="device-capabilities-settings-for-cellular"></a>Definições das capacidades do dispositivo para a rede móvel
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir chamadas em roaming**|Permitir chamadas em roaming quando o dispositivo estiver numa rede celular.|
|**Permitir roaming de dados**|Permite o roaming de dados quando o dispositivo estiver numa rede celular.|
|**Permitir obtenção global em segundo plano em roaming**|Permitir que o dispositivo obtenha dados, tais como e-mail, enquanto estiver em roaming numa rede celular.|

### <a name="device-capabilities-settings-for-features"></a>Definições das capacidades do dispositivo para funcionalidades
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a Siri**|Permitir a utilização do assistente de voz Siri no dispositivo.|
|**Permitir a Siri quando o dispositivo está bloqueado**|Permitir a utilização do assistente de voz Siri no dispositivo enquanto está bloqueado.|
|**Permitir marcação por voz**|Permitir a utilização da funcionalidade de marcação por voz no dispositivo.|
|**Não permitir Airdrop de aplicações geridas**|Faz com que as aplicações geridas não consigam enviar dados através de. Airdrop.|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>Definições para aplicações conformes e não conformes
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

As políticas que contêm as definições de aplicações conformes e não conformes têm de ser implementadas em grupos de utilizadores.

### <a name="kiosk-mode-settings"></a>Definições do modo de local público

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
|**Ativar o zoom**|Ativar ou desativar a definição de acessibilidade **Zoom**, o que permite ao utilizador tocar para aplicar zoom no ecrã do dispositivo.|
|**Ativar os ajustes do zoom**|Ativar ou desativar os ajustes do Zoom, o que permite ao utilizador ajustar a função Zoom.|
|**Ativar a funcionalidade inverter cores**|Ativar ou desativar a definição de acessibilidade **Inverter cores**, que ajusta o ecrã para ajudar os utilizadores com deficiências visuais.|
|**Ativar os ajustes da funcionalidade inverter cores**|Ativar ou desativar a funcionalidade de inverter ajustes de cores, o que permite ao utilizador ajustar a função Inverter Cores.|
|**Ativar o AssistiveTouch**|Ativar ou desativar a definição de acessibilidade **AssistiveTouch**, que ajuda o utilizador a executar gestos no ecrã que lhes poderão ser difíceis de efetuar.|
|**Ativar os ajustes do AssistiveTouch**|Ativar ou desativar os ajustes do AssistiveTouch, o que permite ao utilizador ajustar a função AssistiveTouch.|
|**Ativar a funcionalidade Seleção de voz**|Ativar ou desativar a definição de acessibilidade **Enunciar Seleção**, que lê em voz alta o texto que o utilizador seleciona.|
> [!NOTE]
> As seguintes notas aplicam-se às definições do modo de local público para dispositivos iOS:
>
> -   Antes de poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a [ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) ou o [Programa de Inscrição de Dispositivos Apple](ios-device-enrollment-program-in-microsoft-intune.md) para colocar o dispositivo no modo supervisionado. Para obter mais informações sobre a Ferramenta Apple Configurator, consulte a sua documentação da Apple.
> -   Se a aplicação iOS que especificou for instalada após a implementação da política de configuração, o dispositivo só entrará em modo de local público após ser reiniciado.

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Informações de referência para aplicações conformes e não conformes

Utilize o **Relatório de Aplicações Não Conformes** para ver a conformidade das aplicações permitidas e bloqueadas.

##### <a name="to-run-the-noncompliant-apps-report"></a>Para executar o Relatório de Aplicações Não Conformes

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Relatórios** &gt; **Relatório de Aplicações Não Conformes**.

2.  Selecione os grupos de dispositivos que pretende verificar, selecione se pretende verificar as aplicações compatíveis, as aplicações não compatíveis ou ambas e, em seguida, selecione **Ver Relatório**.

#### <a name="how-to-specify-urls-to-app-stores"></a>Como especificar URLs para lojas de aplicações
Para especificar o URL de uma aplicação na lista de aplicações compatíveis e não compatíveis ou na opção **Selecionar uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público** (apenas em iOS), utilize o seguinte formato:

1. Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.

2. Copie o URL da página e utilize-o como o URL para configurar a lista das aplicações compatíveis ou não compatíveis que pretende executar no modo de local público.

**Exemplo:** Procure por **Microsoft Word para iPad**. O URL que irá utilizar será **https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Também pode utilizar o software iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.

### <a name="enrollment-settings"></a>Definições de inscrição
As definições aplicam-se ao iOS 8.0 e posterior.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir Bloqueio de Ativação quando o dispositivo estiver no modo supervisionado**|Ativar o Bloqueio de Ativação em dispositivos iOS supervisionados.|

### <a name="supervised-mode-settings"></a>Definições do modo supervisionado
Pode configurar as seguintes definições em dispositivos com iOS 8.0 e posterior que estejam no modo supervisionado.

### <a name="supervised-mode-settings-for-device-restrictions"></a>Definições do modo supervisionado para restrições do dispositivo

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir modificação da conta**|Permitir que o utilizador alterar as definições de conta, tais como configurações de e-mail.|
|**Permitir alterações às definições de utilização de dados via rede móvel da aplicação**|Permitir que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.|
|**Permitir a utilização das opções apagar todos os conteúdos e definições do dispositivo**|Permitir que o utilizador utilize a opção de apagar todos os conteúdos e definições do dispositivo.|
|**Permitir que o utilizador ative restrições nas definições do dispositivo**|Permitir que o utilizador configure as restrições de dispositivo (restrições de acesso) no dispositivo.|
|**Permitir emparelhamento de anfitrião para controlar os dispositivos aos quais um dispositivo iOS pode estar emparelhado**|Permitir o emparelhamento de anfitrião para permitir ao administrador o controlo sobre os dispositivos com os quais um dispositivo iOS pode ser emparelhado.|
|**Permitir que o utilizador instale perfis e certificados de configuração**|Permitir que o utilizador instale perfis e certificados de configuração.|
|**Permitir a modificação do nome do dispositivo**|Permitir que o utilizador altere o nome do dispositivo.|
|**Permitir a modificação do código de acesso**|Permitir que a palavra-passe do dispositivo seja adicionada, alterada ou removida.|
|**Permitir o emparelhamento do Apple Watch**|Permitir que o dispositivo emparelhe com um Apple Watch.|
|**Permitir a modificação das definições de notificação**|Permitir que o utilizador altere as definições de notificação do dispositivo.|
|**Permitir a modificação da imagem de fundo**|Permitir que o utilizador altere a imagem de fundo do dispositivo.|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>Definições do modo supervisionado para restrições de funcionalidade

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir AirDrop**|Permitir a utilização da funcionalidade AirDrop para trocar conteúdos com dispositivos que se encontrem próximos.|
|**Permitir que a Siri consulte conteúdos gerados pelo utilizador a partir da Internet**|Permitir que a Siri aceda a sites para responder a perguntas.|
|**Utilizar o filtro de linguagem inapropriada da Siri**|Impede que a Siri dite ou fale com linguagem profana.|
|**Permitir a pesquisa Spotlight para devolver resultados da Internet**|Permitir a ligação da pesquisa Spotlight à Internet para fornecer mais resultados.|
|**Permitir a pesquisa de definição de palavras**|Permitir a funcionalidade do iOS que permite realçar uma palavra e procurar a respetiva definição.|
|**Permitir teclados preditivos**|Permitir a utilização de teclados preditivos que sugerem palavras que o utilizador poderá querer utilizar.|
|**Permitir a correção automática**|Permite que o dispositivo corrija automaticamente palavras com erros ortográficos.|
|**Permitir a verificação ortográfica no teclado**|Permitir o corretor ortográfico do dispositivo.|
|**Permitir atalhos de teclado**|Permitir a utilização de atalhos de teclado.|

### <a name="supervised-mode-settings-for-app-restrictions"></a>Definições do modo supervisionado para restrições de aplicações

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir a modificação das definições de confiança de aplicações empresariais**|Permite que os utilizadores alterem as definições de fidedignidade de aplicações empresariais.|
|**Permitir a instalação de aplicações apenas com a Configuração da Apple e o iTunes**|Ativa ou desativa a App Store a partir do ecrã principal do dispositivo. Os utilizadores ainda podem utilizar o iTunes ou a ferramenta Apple Configurator para instalar e atualizar aplicações.|
|**Permitir transferências automáticas de aplicações**|Permite que aplicações compradas noutros dispositivos sejam automaticamente transferidas para este dispositivo. Esta definição não afeta as atualizações da aplicação.|
|**Permitir alterações para as definições da aplicação Encontrar Amigos**|Permitir que o utilizador altere as definições da aplicação Encontrar Amigos.|
|**Permitir acesso à loja iBooks**|Permitir que o utilizador procure e compre livros da loja iBooks.|
|**Permitir a utilização da aplicação Mensagens no dispositivo**|Permitir a utilização da aplicação Mensagens para enviar mensagens de texto.|
|**Permitir a utilização de Podcasts**|Permitir a utilização de aplicações Podcasts.|
|**Permitir a utilização do serviço de Música**|Permitir a utilização da aplicação Apple Music.|
|**Permitir o serviço iTunes Radio**|Permita a utilização da aplicação iTunes Radio.|
|**Permitir Apple News**|Permita a utilização da aplicação Apple News.|
|**Permitir Game Center**|Permitir utilização da aplicação Game Center.|


### <a name="show-or-hide-apps"></a>Mostrar ou Ocultar Aplicações

Utilize a **Lista de aplicações ocultas e apresentadas** para controlar o seguinte nos dispositivos supervisionados com o iOS 9.3 ou posterior:

- Especificar uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
- Especificar uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>Como criar uma lista de aplicações ocultas ou apresentadas

Especifique as seguintes definições:

|Nome da definição|Detalhes|
|-|-|
|**Lista de aplicações ocultas e apresentadas**|Ative esta definição se pretender criar uma lista de aplicações ocultas ou apresentadas.|
|**Ocultar dos utilizadores as aplicações listadas**|Selecione esta opção se pretender criar uma lista de aplicações que serão ocultadas dos utilizadores.<br>Quando cria este tipo de lista, todas as aplicações, exceto para **Definições** e **Telefone** (para iPhones) do iOS podem ser ocultadas.|
|**Mostrar aos utilizadores apenas as aplicações listadas**|Selecione esta opção se pretender criar uma lista de aplicações que serão apresentadas aos utilizadores.<br>Quando cria este tipo de lista, todas as outras aplicações, exceto para **Definições** e **Telefone** (para iPhones) do iOS, estão ocultadas.<br>Além disso, tem de adicionar o Portal da Empresa e todas as aplicações que tiver implementado e que gere com o Intune à lista.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada.<br>Em relação à lista oculta, tem de especificar o **Nome**, **Publicador** e **URL da Aplicação ou ID do Pacote** de cada aplicação que pretende ocultar.<br>Para obter a lista apresentada, pode **Selecionar uma aplicação gerida** que fornece uma lista das aplicações que gere com o Intune para seleção ou Selecionar uma aplicação de loja, tendo de especificar em seguida o **Nome**, **Publicador**e **URL da Aplicação ou ID do Pacote** de cada aplicação que pretende apresentar.|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|

#### <a name="app-information-for-built-in-ios-apps"></a>Informações para aplicações iOS incorporadas

Utilize as informações nesta lista para identificar o nome, o publicador e o ID das aplicações iOS incorporadas que pretenda mostrar ou ocultar. Se pretender mostrar ou ocultar todas as aplicações na lista, pode copiar os dados abaixo para um ficheiro de texto com a extensão **.csv** e, em seguida, utilizar a opção **Importar Aplicações** para importar todas as aplicações em simultâneo.

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
,com.apple.mobilesafariSafari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple


```




## <a name="custom-policy-settings"></a>Definições de política personalizada

Utilizar a **política personalizada do iOS** do Microsoft Intune para implementar as definições que criou utilizando a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) para dispositivos iOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para uma política personalizada do iOS do Intune e implementar as definições em utilizadores e dispositivos da sua organização.

Esta capacidade permite-lhe a implementação de definições do iOS que não são configuráveis com as políticas de configuração gerais do Intune.

### <a name="prerequisites"></a>Pré-requisitos
Antes de começar, tem de ter instalado o Apple Configurator e criar um ficheiro de configuração que contém as definições que pretende implementar nos utilizadores ou dispositivos. Pode transferir e obter informações sobre o Apple Configurator na [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> O Intune não comunica a conformidade de definições individuais em políticas personalizadas do iOS. No entanto, a conformidade geral das políticas é comunicada.

### <a name="general-settings"></a>Definições gerais

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política personalizada do iOS para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Indique uma descrição geral da política personalizada do iOS e outras informações relevantes que o ajudem a localizá-la.|

### <a name="custom-settings"></a>Definições personalizadas

|Nome da definição|Detalhes|
    |----------------|--------------------|
|**Nome do perfil de configuração personalizado (apresentado aos utilizadores)**|Indique um nome para a política tal como será apresentado no dispositivo e nos relatórios de políticas do Intune.|
|**Ficheiro de perfil de configuração**|Escolha **Importar** e em seguida, navegue até ao perfil de configuração que criou ao utilizar o Apple Configurator. **Nota:** Certifique-se de que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do iOS nos dispositivos nos quais implementou a política personalizada do iOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no site [Apple Developer](https://developer.apple.com/).|
    |**Detalhes do perfil de configuração**|Apresentar o código XML do perfil de configuração que importou.|

### <a name="see-also"></a>Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
