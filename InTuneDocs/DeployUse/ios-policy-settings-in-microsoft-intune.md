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
ms.sourcegitcommit: 947328a5c28839d8227a9e5ae0dd8b1fc5ad8e81
ms.openlocfilehash: 63bc2cedf8d81b050a384a947a0b43827de5c352


---

# Definições de política do iOS no Microsoft Intune

O Intune fornece uma variedade de definições gerais incorporadas, que pode configurar em dispositivos iOS. Além disso, pode utilizar a ferramenta Apple Configurator para criar definições personalizadas que não estão disponíveis no Intune.

## Definições de política de configuração geral

Utilize a **política de configuração geral do iOS** do Microsoft Intune para configurar definições para:

-   **Definições de segurança do dispositivo móvel** – Escolha a partir de uma lista de definições predefinidas que permitem controlar uma série de funcionalidades e a funcionalidade no dispositivo.

-   **Modo de local público** - Bloqueie um dispositivo para que apenas algumas funcionalidades possam ser utilizadas. Por exemplo, pode permitir que um dispositivo execute apenas uma aplicação gerida que especificar ou pode desativar os botões de volume num dispositivo. Estas definições podem ser utilizadas para um modelo de demonstração de um dispositivo ou para um dispositivo com a finalidade de desempenhar apenas uma função, como um dispositivo de ponto de venda.

-   **Aplicações compatíveis e não compatíveis** - Especifique uma lista de aplicações que são compatíveis ou não compatíveis na sua empresa. Em dispositivos Android e iOS, o **Relatório de Aplicações Não Compatíveis** pode ser utilizado para ver a compatibilidade de aplicações especificadas na lista comparativamente às aplicações instaladas pelos utilizadores (mas não pode bloquear a instalação da aplicação).

> [!TIP]
> Pode configurar termos e condições para os utilizadores, para garantir que estes têm conhecimento de que as aplicações nos respetivos dispositivos, incluindo aplicações pessoais, serão avaliadas e que as aplicações não compatíveis serão bloqueadas ou comunicadas como não compatíveis. Os utilizadores têm de aceitar estes termos e condições antes de poderem inscrever os respetivos dispositivos e utilizar o portal da empresa para obter aplicações. Para obter mais informações sobre como utilizar os termos e condições, consulte [Definições de políticas de termos e condições no Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se a definição que procura não aparecer neste tópico, poderá conseguir criá-la utilizando uma política personalizada de iOS que permita importar as definições que criou com a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para mais informações, consulte **Definições de política personalizada** mais adiante neste tópico.

### Definições de segurança
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Palavra-passe obrigatória para desbloquear os dispositivos móveis**|Especifica se os utilizadores são obrigados a introduzir uma palavra-passe para aceder ao respetivo dispositivo.|
|**Tipo obrigatório de palavra-passe**|Especifica o tipo de palavra-passe que será necessária, como apenas numérica ou alfanumérica.|
|**Número de carateres complexos necessários na palavra-passe**|Isto especifica o número de caracteres de símbolos (como **#** ou **@**) que têm de ser incluídos na palavra-passe.|
|**Comprimento mínimo da palavra-passe**|Especifica o número mínimo de carateres na palavra-passe.|
|**Permitir palavras-passe simples**|Permite palavras-passe simples, como «0000» e «1234».|
|**Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado**|Apaga o dispositivo em caso de falha deste número de tentativas de início de sessão.|
|**Minutos de inatividade antes de ser exigida a palavra-passe**<sup>1</sup>|Especifica o período de tempo durante o qual o dispositivo pode permanecer inativo antes de o utilizador ter de reintroduzir a palavra-passe.|
|**Expiração da Palavra-passe (dias)**|Especifica o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.|
|**Memorizar histórico de palavras-passe**|Especifica se o utilizador pode utilizar palavras-passe que utilizou anteriormente.|
|**Memorizar histórico de palavras-passe** – **Evita a reutilização de palavras-passe anteriores**|Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.|
|**Minutos de inatividade antes de o ecrã se desligar**<sup>1</sup>|Especifique o número de minutos antes de o ecrã do dispositivo se desligar.|
|**Permitir desbloqueio por impressão digital**|Permite a utilização de uma impressão digital para desbloquear o dispositivo.|
<sup>1</sup> Para dispositivos iOS, quando configura as definições **Minutos de inatividade antes de o ecrã se desligar** e **Minutos de inatividade antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, o ecrã desliga-se automaticamente após 5 minutos e o dispositivo fica bloqueado após mais 5 minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois de o utilizador desligar o ecrã, o dispositivo bloqueia 5 minutos depois.

### Definições do sistema
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir captura de ecrã**|Permite ao utilizador capturar o conteúdo do ecrã como uma imagem.|
|**Permitir centro de controlo no ecrã de bloqueio**|Controla se a aplicação do centro de controlo pode ser acedida quando o dispositivo está bloqueado.|
|**Permitir vista de notificações no ecrã de bloqueio**|Permite que o utilizador aceda à vista de notificações sem desbloquear o dispositivo.|
|**Permitir vista atual no ecrã de bloqueio**|Controla se as notificações podem ser visualizadas quando o dispositivo está bloqueado.|
|**Permitir certificados TLS não fidedignos**|Permitir certificados Transport Layer Security não fidedignos no dispositivo.|
|**Permitir submissão de dados de diagnóstico**|Permitir ou impedir o dispositivo de submeter dados de diagnóstico para a Apple.|
|**Permitir passbook quando bloqueado**|Permitir que o utilizador aceda à aplicação Passbook quando o dispositivo está bloqueado.|

### Definições da nuvem - documentos e dados
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir cópia de segurança para iCloud**|Permite que o utilizador faça uma cópia de segurança do dispositivo para o iCloud.|
|**Permitir sincronização de documentos para iCloud**|Permitir a sincronização de documentos e pares chave-valor para o seu espaço de armazenamento do iCloud.|
|**Permitir sincronização de Fluxo de Fotografias para iCloud**|Permitir a sincronização das fotografias no dispositivo com o iCloud.|
|**Exigir cópia de segurança encriptada**|Exigir que qualquer cópia de segurança seja encriptada.|
|**Permitir que as aplicações geridas sincronizem dados para o serviço iCloud**|Permitir que as aplicações que gere com o Intune sincronizem dados para a conta do iCloud dos utilizadores.|
|**Permitir que o Handoff continue as atividades noutro dispositivo**|O Handoff permite-lhe continuar o trabalho iniciado num dispositivo iOS noutro dispositivo iOS ou Mac OS X.|

### Definições da aplicação - browser
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir o Safari**|Especificar se o browser Safari pode ser utilizado no dispositivo.|
|**Permitir preenchimento automático**|O utilizador pode alterar as definições de conclusão automática no browser.|
|**Permitir bloqueador de janelas de pop-up**|Ativar ou desativar o bloqueador de janelas de pop-up do browser.|
|**Permitir cookies**|Permitir que o browser do dispositivo utilize cookies.|
|**Permitir scripting de Java**|Permitir a execução de scripts de Java no browser.|
|**Permitir aviso de fraude**|Permitir avisos de fraude no browser do dispositivo.|

### Definições da aplicação - aplicações
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir loja de aplicações**|Permite que o dispositivo aceda à loja de aplicações.|
|**Exigir uma palavra-passe para aceder à loja de aplicações**|Exige que o utilizador introduza uma palavra-passe antes de poderem visitar a loja de aplicações.|
|**Permitir compras via aplicação**|Permite efetuar compras na loja a partir de uma aplicação em execução.|
|**Permitir documentos geridos em outras aplicações não geridas**|Permite a visualização de documentos da empresa em qualquer aplicação.<br>**Exemplo:** pretende impedir que os utilizadores guardem os ficheiros da aplicação OneDrive no Dropbox. Configure esta definição como não. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não será permitido guardar.|
|**Permitir documentos não geridos em outras aplicações geridas**|Permitir a visualização de qualquer documento em aplicações geridas empresariais.|
|**Permitir videoconferência**|Permitir aplicações de videoconferência, tal como o Facetime, no dispositivo.|
|**Permitir conteúdo para adultos no arquivo de multimédia**|Permitir que o dispositivo aceda a conteúdo da loja classificado como conteúdo para adultos.|
|**Permitir que o utilizador transfira conteúdos da loja iBook sinalizado como "Erótico"**|Permitir que o utilizador transferir livros da categoria "Erótico".|

### Definições da aplicação - Jogos
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a adição de amigos do Centro de Jogos**|Permitir que o utilizador adicione amigos no Centro de jogos.|
|**Permitir jogos multijogador**|Permitir que o utilizador jogue jogos multijogador no dispositivo.|

### Definições das capacidades do dispositivo - hardware
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir câmara**|Especifica se a câmara do dispositivo pode ser utilizada.|
|**Requerer palavra-passe emparelhada para os pedidos AirPlay enviados**|O Airplay permite-lhe transmitir conteúdos para outros dispositivos Apple. Utilize esta definição para requerer uma palavra-passe emparelhada para ligar-se a outros dispositivos.|

### Definições das capacidades do dispositivo - rede móvel
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir chamadas em roaming**|Permitir chamadas em roaming quando o dispositivo estiver numa rede celular.|
|**Permitir roaming de dados**|Permite o roaming de dados quando o dispositivo estiver numa rede celular.|
|**Permitir obtenção global em segundo plano em roaming**|Permitir que o dispositivo obtenha dados, tais como e-mail, enquanto estiver em roaming numa rede celular.|

### Definições das capacidades do dispositivo - funcionalidades
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|-------|
|**Permitir a Siri**|Permitir a utilização do assistente de voz Siri no dispositivo.|
|**Permitir a Siri quando o dispositivo está bloqueado**|Permitir a utilização do assistente de voz Siri no dispositivo enquanto está bloqueado.|
|**Permitir marcação por voz**|Permitir a utilização da funcionalidade de marcação por voz no dispositivo.|


### Definições para aplicações compatíveis e não compatíveis
Na lista **Aplicações Conformes e &amp;Não Conformes**, especifique uma lista de aplicações conformes ou não conformes com as informações seguintes:

> [!NOTE]
> Uma única política só pode conter uma lista de aplicações compatíveis ou uma lista de aplicações não compatíveis. Não é possível especificar ambas na mesma política.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Comunicar não conformidade quando os utilizadores instalam as aplicações listadas**|Indica as aplicações que não são geridas pelo Intune e para as quais os utilizadores não têm permissão para instalar e executar.|
|**Comunicar não conformidade quando os utilizadores instalam aplicações não listadas**|Indica as aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não têm de instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas.|
|**Adicionar**|Adiciona uma aplicação à lista selecionada. Especifique um nome à sua escolha, o fabricante da aplicação (opcional) e o URL para a aplicação na loja de aplicações. Para obter mais ajuda, leia **Como especificar URLs para lojas de aplicações** mais adiante neste tópico.|
|**Importar Aplicações**|Importa uma lista de aplicações especificadas num ficheiro de valores separados por vírgulas. Utilize o formato, o nome da aplicação, o fabricante e o URL da aplicação no ficheiro.|
|**Editar**|Permite-lhe editar o nome, o fabricante e o URL da aplicação selecionada.|
|**Eliminar**|Elimina a aplicação selecionada da lista.|

### Definições do modo de local público

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Selecione uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público**|Selecione **Procurar**e, em seguida, especifique a aplicação gerida ou a aplicação de uma loja que terá permissão para ser executada quando o dispositivo estiver em modo de local público. Não será permitida a execução de outras aplicações no dispositivo. Para obter mais ajuda, consulte **Como especificar URLs para lojas de aplicações** mais adiante neste tópico.|
|**Permitir toque**|Ativa ou desativa o ecrã tátil do dispositivo.|
|**Permitir a rotação do ecrã**|Ativa ou desativa a mudança da orientação do ecrã ao rodar o dispositivo.|
|**Permitir os botões de volume**|Ativa ou desativa a utilização dos botões de volume no dispositivo.|
|**Permitir a alteração do toque**|Ativa ou desativa a alteração do toque (desativar som) no dispositivo.|
|**Permitir o botão suspender/reativar ecrã**|Ativa ou desativa o botão suspender/reativar ecrã do dispositivo.|
|**Permitir o bloqueio automático**|Ativa ou desativa o bloqueio automático do dispositivo.|
|**Ativar o áudio mono**|Ativa ou desativa a definição de acessibilidade **Áudio mono**.|
|**Ativar o VoiceOver**|Ativa ou desativa a definição de acessibilidade **VoiceOver** , que lê em voz alta o texto no ecrã do dispositivo.|
|**Ativar ajustes do VoiceOver**|Ativa ou desativa os ajustes do VoiceOver, o que lhe permite ajustar a função VoiceOver (por exemplo, a rapidez de leitura em voz alta do texto no ecrã).|
|**Ativar o Zoom**|Ativa ou desativa a definição de acessibilidade **Zoom** , o que lhe permite tocar para aplicar zoom no ecrã do dispositivo.|
|**Ativar os ajustes do Zoom**|Ativa ou desativa os ajustes do Zoom, o que lhe permite ajustar a função Zoom.|
|**Ativar a funcionalidade Inverter Cores**|Ativa ou desativa a definição de acessibilidade **Inverter Cores** , que ajusta o ecrã para ajudar utilizadores com deficiências visuais.|
|**Ativar os ajustes da funcionalidade Inverter Cores**|Ativa ou desativa os ajustes da funcionalidade Inverter Cores, o que lhe permite ajustar a função Inverter Cores.|
|**Ativar o AssistiveTouch**|Ativa ou desativa a definição de acessibilidade **AssistiveTouch** , que ajuda os utilizadores a executar gestos no ecrã que lhes poderão ser difíceis.|
|**Ativar os ajustes do AssistiveTouch**|Ativa ou desativa os ajustes do AssistiveTouch, o que lhe permite ajustar a função AssistiveTouch.|
|**Ativar a funcionalidade Enunciar seleção**|Ativa ou desativa a definição de acessibilidade **Enunciar seleção** , que lê em voz alta o texto que selecionou.|
> [!NOTE]
> As seguintes notas aplicam-se às definições do modo de local público para dispositivos iOS:
> 
> -   Antes de poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a [Ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) ou o gestor de inscrição de dispositivos para colocar o dispositivo em modo supervisionado. Para obter mais informações sobre a Ferramenta Apple Configurator, consulte a sua documentação da Apple.
> -   Se a aplicação iOS especificada for instalada após a implementação da política de configuração, o dispositivo só entrará em modo de local público após ser reiniciado.

### Informações de referência para aplicações compatíveis e não compatíveis

#### Monitorizar aplicações compatíveis e não compatíveis
Utilize o **Relatório de Aplicações Não Compatíveis** para ver a compatibilidade das aplicações permitidas e bloqueadas.

##### Para executar o Relatório de Aplicações Não Compatíveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Relatórios** &gt; **Relatório de Aplicações Não Compatíveis**.

2.  Selecione os grupos de dispositivos que pretende verificar, se pretende verificar as aplicações compatíveis, as aplicações não compatíveis ou ambas e, em seguida, selecione **Ver Relatório**.

#### Como especificar URLs para lojas de aplicações
Para especificar o URL de uma aplicação na lista de aplicações compatíveis e não compatíveis ou na opção **Selecionar uma aplicação gerida que terá permissão para ser executada quando o dispositivo estiver em modo de local público** (apenas em iOS), utilize o seguinte formato:

Através de um motor de pesquisa, localize a aplicação que pretende utilizar na App Store do iTunes e abra a página da aplicação.

Copie o URL da página e utilize-o para configurar a lista de aplicações compatíveis e não compatíveis ou a aplicação que pretende executar em modo de lugar público.

**Exemplo:** Procure por **Microsoft Word para iPad**. O URL a utilizar será **https://itunes.apple.com/pt/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Também pode utilizar o software iTunes para localizar a aplicação e, em seguida, utilizar o comando **Copiar Ligação** para obter o URL da aplicação.

### Definições de inscrição
Todas as definições se aplicam ao iOS 7.1 e posterior.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir Bloqueio de Ativação quando o dispositivo estiver no modo supervisionado**|Ativa o Bloqueio de Ativação em dispositivos iOS supervisionados.|

### Supervisão
As seguintes definições podem ser configuradas em dispositivos com iOS 7.1 e posterior que estejam no modo supervisionado.

|Nome da definição|Detalhes|
|----------------|--------------------|
|**Permitir modificação da conta**|Permitir que o utilizador alterar as definições de conta, tais como configurações de e-mail.|
|**Permitir AirDrop**|Permita a utilização da funcionalidade Airdrop para trocar conteúdos com dispositivos que se encontrem próximos.|
|**Permitir alterações às definições de utilização de dados via rede móvel da aplicação**|Permitir que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.|
|**Permitir que a Siri consulte conteúdos gerados pelo utilizador a partir da Internet**|Permitir que a Siri aceda a sites para responder a perguntas.|
|**Permitir acesso à loja iBooks**|Permitir que o utilizador procure e compre livros da loja iBooks.|
|**Permitir alterações para as definições da aplicação Encontrar Amigos**|Permitir que o utilizador altere as definições da aplicação Encontrar Amigos.|
|**Permitir a utilização das opções apagar todos os conteúdos e definições do dispositivo**|Permitir que o utilizador utilize as opções apagar todos os conteúdos e definições do dispositivo.|
|**Permitir que o utilizador ative restrições nas definições do dispositivo**|Permitir que o utilizador configure as restrições de dispositivo (restrições de acesso) no dispositivo|
|**Permitir a pesquisa Spotlight para devolver resultados da Internet**|Vamos ligar a pesquisa Spotlight à Internet para fornecer mais resultados.|
|**Permitir a utilização da aplicação Game Center**|Permitir utilização da aplicação Game Center.|
|**Permitir emparelhamento de anfitrião para controlar os dispositivos aos quais um dispositivo iOS pode estar emparelhado**|O emparelhamento de anfitrião permite ao administrador controlar com que dispositivos um dispositivo iOS 7 pode ser emparelhado.|
|**Permitir que o utilizador instale perfis e certificados de configuração**|Permitir que o utilizador instale perfis e certificados de configuração.|
|**Permitir a utilização da aplicação Mensagens no dispositivo**|Permitir a utilização da aplicação Mensagens para enviar mensagens de texto.|


## Definições de política personalizada

Utilize a **política personalizada do iOS** do Microsoft Intune para implementar definições criadas com a [ferramenta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) em dispositivos iOS. Esta ferramenta permite criar muitas definições que controlam o funcionamento destes dispositivos e exportá-las para um perfil de configuração. Em seguida, pode importar este perfil de configuração para uma política personalizada do iOS do Intune e implementar as definições em utilizadores e dispositivos da sua organização.

Esta capacidade destina-se a permitir a implementação de definições do iOS que não são configuráveis com as políticas de configuração geral do Intune.

### Pré-requisitos
Antes de começar, tem de ter instalado o Apple Configurator e criar um ficheiro de configuração com as definições que pretende implementar nos utilizadores ou dispositivos. Pode transferir e obter informações sobre o Apple Configurator na [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)

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
|**Ficheiro de perfil de configuração**|Selecione **Importar** e, em seguida, navegue até ao perfil de configuração que criou com o Apple Configurator. **Nota:** Certifique-se de que as definições exportadas a partir da ferramenta Apple Configurator são compatíveis com a versão do iOS nos dispositivos nos quais implementou a política personalizada do iOS. Para obter informações sobre como são resolvidas as definições incompatíveis, pesquise **Configuration Profile Reference** (Referência de Perfil de Configuração) e **Mobile Device Management Protocol Reference** (Referência do Protocolo de Gestão de Dispositivos Móveis) no Web site [Apple Developer](https://developer.apple.com/).|
    |**Detalhes do perfil de configuração**|Apresenta o código XML do perfil de configuração que importou.|

### Consulte também
[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO4-->


