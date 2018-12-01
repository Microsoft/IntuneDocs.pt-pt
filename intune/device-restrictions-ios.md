---
title: Adicionar definições de restrições de dispositivos iOS no Microsoft Intune – Azure | Documentos da Microsoft
titleSuffix: ''
description: Adicionar, configurar, ou criar definições em dispositivos iOS para definir os requisitos de palavra-passe, controlar o ecrã bloqueado, utilize aplicações incorporadas, adicionar restrito ou aplicações aprovadas, lidar com dispositivos bluetooth, ligar para a cloud na cópia de segurança e armazenamento, ativar o modo de local público, adicionar domínios, e controle como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a677742c5d2f876c0714f13c4f62d059ced98584
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728978"
---
# <a name="ios-device-restrictions-settings-list-in-microsoft-intune"></a>lista as definições de restrições de dispositivos do iOS no Microsoft Intune

Este artigo apresenta e descreve todas as definições de restrição de dispositivos que pode configurar para dispositivos iOS. Estas definições são adicionadas a um perfil de configuração do dispositivo e, em seguida, atribuídas ou implementadas nos seus dispositivos iOS com o Microsoft Intune.

## <a name="general"></a>Geral

- **Partilhar dados de utilização**: escolha **bloco** para impedir que o dispositivo de enviar dados de diagnóstico e utilização para a Apple. **Não configurado** permite que estes dados a serem enviados.
  - **Submissão de dados de diagnóstico**: **bloco** impede que o utilizador alterar as definições de análise de submissão e aplicação de diagnóstico no **diagnóstico e utilização** (definições de dispositivo). Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado (iOS 9.3.2 +). **Não configurado** permite ao utilizador alterar estas definições do dispositivo.
- **Captura de ecrã**: escolha **bloco** para impedir capturas de ecrã ou ecrã capturas no dispositivo. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
  - **Observação remota do ecrã pela aplicação Classroom (apenas supervisionada)**: escolha **bloco** para impedir que a aplicação sala de aula remotamente, ver o ecrã no dispositivo. Para utilizar esta definição, o dispositivo tem de estar no modo supervisionado (iOS 9.3 +). **Não configurado** permite que a aplicação sala de aula da Apple ver o ecrã.
  - **Observação não solicitada do ecrã através da aplicação Classroom (apenas supervisionado)**: se definido como **permitir**, professores podem observar silenciosamente o ecrã de dispositivos iOS de estudantes através da aplicação Classroom sem o conhecimento dos estudantes. Dispositivos de estudantes inscritos numa classe com a aplicação de sala de aula automaticamente conceder permissão ao professor do curso. **Não configurado** impede que esta funcionalidade.
- **Certificados TLS não fidedignos**: escolha **bloco** para impedir que os certificados Transport Layer Security (TLS) não fidedignos no dispositivo. **Não configurado** permite que os certificados TLS.
- **Fidedignidade da aplicação empresarial**: escolha **bloco** para remover o **Trust Enterprise Developer** botão em Definições > geral > perfis e gestão de dispositivos no dispositivo. **Não configurado** permite que o utilizador optar por confiar em aplicações que não são transferidas a partir da loja de aplicações.
- **Modificação da conta (apenas supervisionado)**: Quando definido como **bloco**, o utilizador não é possível atualizar as definições específicas do dispositivo a partir da aplicação de definições do iOS. Por exemplo, o utilizador não é possível criar novas contas de dispositivo, ou alterar o nome de utilizador ou palavra-passe. **Não configurado** permite que os usuários alterar estas definições.
  Esta funcionalidade também aplica-se às definições acessíveis a partir da aplicação de definições de iOS, por exemplo, correio, contactos, calendário, Twitter e muito mais. Esta funcionalidade não se aplica a aplicações com as definições da conta que não são configuráveis a partir da aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.
- **Ativar restrições nas definições do dispositivo (apenas supervisionadas)**: escolha **bloco** para impedir que os utilizadores ativar restrições nas definições do dispositivo. **Não configurado** permite que o usuário configurar restrições de dispositivos (por exemplo, restrições de acesso) no dispositivo.
- **Utilização de apagar opção todos os conteúdos e definições no dispositivo (apenas supervisionado)**: escolha **bloco** para que os utilizadores não é possível utilizar a opção de definições no dispositivo (apenas supervisionado) e apagar todos os conteúdos. **Não configurado** dá aos utilizadores acesso a estas definições.
- **Modificação do nome do dispositivo (apenas supervisionada)**: escolha **bloco** para que não é possível alterar o nome do dispositivo. **Não configurado** permite ao utilizador alterar o nome do dispositivo.
- **Modificação de definições de notificação (apenas supervisionada)**: escolha **bloco** para que não não possível alterar as definições de notificação. **Não configurado** permite que o utilizador altere as definições de notificação do dispositivo.
- **Imagem de fundo (apenas supervisionado)**: **bloco** impede que a imagem de fundo que está a ser alterado. **Não configurado** permite que o utilizador altere a imagem de fundo no dispositivo.
- **(Apenas supervisionado) dos modificação de definições de confiança para aplicações empresariais**: **bloco** impede o utilizador alterar as definições de fidedignidade de aplicações empresariais em dispositivos supervisionados. **Não configurado** permite ao utilizador confiar em aplicações que não são transferidas a partir da loja de aplicações.
- **Alterações do perfil de configuração (apenas supervisionadas)**: **bloco** impede alterações do perfil de configuração no dispositivo. **Não configurado** permite que o utilizador instale perfis de configuração.
- **Bloqueio de ativação (apenas supervisionado)**: escolha **permitir** ativar o bloqueio de ativação de dispositivos iOS supervisionados. Bloqueio de ativação dificulta que um dispositivo perdido ou roubado ser reativado.
- **Bloquear a remoção de aplicações (apenas supervisionada)**: escolha **bloco** para impedir que os utilizadores a remover aplicações. **Não configurado** permite aos utilizadores remover aplicações do dispositivo.
- **Modo de USB restrito de blocos (apenas supervisionado)**: escolha **bloco** para desativar o modo restrito de USB em dispositivos supervisionados. Modo restrito de USB bloqueia acessórios USB de troca de dados com um dispositivo que está bloqueado para mais de uma hora. **Não configurado** permite que o modo restrito de USB.
- **Forçar automática data e hora (apenas supervisionado)**: **requerem** forças supervisionado dispositivos para definir a data e hora automaticamente. Fuso horário do dispositivo é atualizado quando o dispositivo tem ligações via rede móveis ou ativou Wi-Fi com os serviços de localização.
- **Exigir aos alunos para solicitar permissão para deixar o curso em sala de aula (apenas supervisionado)**: **requerem** força os estudantes inscritos num curso não gerido com a aplicação de sala de aula solicitar permissão do professor sair o curso. Disponível apenas no iOS 11.3 +. **Não configurado** não força o aluno para pedir permissão.
- **Permitir atualizações por ondas eletromagnéticas do PKI**: **permitir** permite aos usuários receber atualizações de software sem precisar se conectar seus dispositivos a um computador.
- **Ad de limite de controlo**: escolha **limite** para desativar o identificador de publicidade do dispositivo. **Não configurado** mantém-a ativada.
- **Criação de VPN de bloco (apenas supervisionada)**: **bloco** impede os utilizadores de criação de definições de configuração de VPN. **Não configurado** permite aos usuários criar VPNs no dispositivo.

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
- Transferências automáticas de aplicações 
- Alterações à confiança na aplicação de empresa 
- Apple Music 
- Mail Drop 
- Emparelhar com o Apple Watch 

> [!NOTE]
> A Apple confirmou que determinadas definições irão mudar para apenas supervisionado em 2019. Recomendamos que tenha isto em consideração ao utilizar estas definições em vez de aguardar que a Apple efetue a migração para apenas supervisionado:
> - Instalação da aplicação por utilizadores finais
> - Remoção de aplicações
> - FaceTime
> - Safari
> - iTunes
> - Conteúdos explícitos
> - Documentos e dados do iCloud
> - Jogos de vários jogadores
> - Adicionar amigos do Game Center
> - Siri

## <a name="password"></a>Palavra-passe

- **Palavra-passe**: exigir que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. Não configurado permite aos utilizadores aceder ao dispositivo sem introduzir uma palavra-passe.
  - **Palavras-passe simples**: escolha **bloco** solicitar palavras-passe mais complexas. **Não configurado** permite que as palavras-passe simples, como `0000` e `1234`.
  - **Tipo de palavra-passe obrigatório**: Escolha o tipo de palavra-passe necessitam da sua organização. As opções são:
    - **Predefinição do dispositivo**
    - **numérico**
    - **Alfanumérico**
  - **Número de carateres não alfanuméricos na palavra-passe**: introduza o número de carateres de símbolo, tal como `#` ou `@`, que têm de ser incluídos na palavra-passe.
  - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo de um utilizador tem de introduzir (entre 4 e 14 caracteres).
  - **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de inícios de sessão falhados a permitir antes do dispositivo ser apagado (entre 1 a 11).
  - **Máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida**<sup>1</sup>: introduza o tempo que o dispositivo permanece inativo antes do utilizador ter de reintroduzir a palavra-passe. Se o tempo que introduzir superior ao atualmente definido no dispositivo, em seguida, o dispositivo ignora o tempo que introduzir. Suportado no iOS 8.0 e dispositivos mais recentes.
  - **Máximo de minutos de inatividade até o ecrã bloquear**<sup>1</sup>: introduza o número máximo de minutos de inatividade permitido no dispositivo até o ecrã ser bloqueado. Se o tempo que introduzir superior ao atualmente definido no dispositivo, em seguida, o dispositivo ignora o tempo que introduzir.
  - **Expiração de palavra-passe (dias)**: introduza o número de dias antes da palavra-passe do dispositivo tem de ser alterada.
  - **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que deve ser usado até que pode ser reutilizada uma antiga.
  - **Desbloqueio por impressão digital**: escolha **bloco** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Modificação do código de acesso (apenas supervisionada)**: escolha **bloco** para parar o código de acesso do que está a ser alterado, adicionado ou removido. Alterações às restrições de código de acesso são ignoradas em dispositivos supervisionados depois de bloqueada a esta funcionalidade. **Não configurado** permite que os códigos de acesso ser adicionado, alteradas ou removidas.
  - **(Apenas supervisionada) de modificação de impressão digital**: **bloco** impede o utilizador alterar, adicionar ou remover impressões digitais TouchID. **Não configurado** permite a atualização do utilizador de impressões digitais TouchID no dispositivo.
- **Palavra-passe de bloco preenchimento automático (apenas supervisionado)**: escolha **bloco** para impedir a utilização da funcionalidade de palavras-passe de preenchimento automático no iOS. Escolher **bloco** também faz o seguinte:
  - Os utilizadores não são-lhe pedidos para utilizar uma palavra-passe guardada no Safari ou em todas as aplicações.
  - Palavras-passe forte de automáticas estão desativadas e as palavras-passe fortes não são sugeridas para os utilizadores.

  **Não configurado** permite que esses recursos.

- **Bloquear pedidos de proximidade de palavra-passe (apenas supervisionados)**: escolha **bloco** para que o dispositivo de um utilizador não solicitar palavras-passe do dispositivos próximos. **Não configurado** permite que estes pedidos de palavra-passe.
- **Bloquear a partilha de palavra-passe (apenas supervisionado)**: **bloco** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** permite que as palavras-passe a ser partilhado.

<sup>1</sup>ao configurar o **máximo de minutos de inatividade até o ecrã bloquear** e **máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida** definições, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, a ecrã desliga automaticamente passados cinco minutos e o dispositivo é bloqueado após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois do utilizador desliga o ecrã, o dispositivo ser bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

- **Acesso de centro de controlo enquanto o dispositivo está bloqueado**: escolha **bloco** para impedir o acesso à aplicação Centro de controlo quando o dispositivo está bloqueado. **Não configurado** permite aos utilizadores acesso à aplicação Centro de controlo quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: **bloco** impede o acesso a notificações quando o dispositivo está bloqueado. **Não configurado** permite ao utilizador aceder as notificações sem desbloquear o dispositivo.
- **Notificações de carteira, enquanto o dispositivo está bloqueado**: **bloco** impede o acesso à aplicação Carteira quando o dispositivo está bloqueado. **Não configurado** permite ao utilizador aceder à aplicação de carteira, enquanto o dispositivo está bloqueado.
- **Vista hoje enquanto o dispositivo está bloqueado**: **bloco** impede o acesso para a vista hoje enquanto o dispositivo está bloqueado. **Não configurado** permite ao utilizador ver a vista hoje enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

- **Loja de aplicações**: **bloco** impede o acesso à loja de aplicações em dispositivos supervisionados. **Não configurado** permite o acesso.
  - **Instalar aplicações da Store da aplicação (apenas supervisionado)**: escolha **bloco** para bloquear a app store a partir do ecrã principal do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** permite que a loja de aplicações no ecrã inicial.
  - **Transferências automáticas de aplicações (apenas supervisionadas)**: escolha **bloco** para impedir a transferência automática de aplicações compradas noutros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** permite que as aplicações compradas noutros dispositivos iOS para transferir no dispositivo.
- **Palavra-passe para aceder à loja de aplicações**: **requerem** ao utilizador para introduzir uma palavra-passe antes de poderem visitar a loja de aplicações. **Não configurado** permite o acesso à loja de aplicações, sem introduzir uma palavra-passe.
- **Compras no aplicativo**: escolha **bloco** para impedir que as compras na aplicação da loja. **Não configurado** permite compras na loja uma aplicação em execução.
- **Conteúdo de música, podcast ou notícias do explícito do iTunes (apenas supervisionado)**: escolha **bloco** para impedir que o conteúdo de música, podcast ou notícias explícito do iTunes. **Não configurado** permite que o dispositivo aceda ao conteúdo classificado como conteúdo para adultos na loja.
- **Transferir conteúdos da iBook store identificados como "Erótico"**: escolha **bloco** para impedir que os utilizadores de deixar de transferir o suporte de dados a partir da iBook store que é identificada como erótica. **Não configurado** permite ao utilizador transferir livros da categoria "Erótico".
- **Ver documentos empresariais em aplicações não geridas**: **bloco** impede a ver documentos não empresariais em aplicações não geridas. **Não configurado** permite que os documentos empresariais sejam vistos em qualquer aplicação. Por exemplo, pretende impedir que os utilizadores guardar ficheiros a partir da aplicação OneDrive no Dropbox. Configurar esta definição como **bloco**. Depois do dispositivo receber a política (por exemplo, após um reinício), já não permite a guardar.
- **Ver documentos não empresariais em aplicações empresariais**: **bloco** impede a ver documentos não empresariais em aplicações empresariais. **Não configurado** permite que qualquer documento seja visto em aplicações geridas empresariais.
- **Tratar o AirDrop como um destino não gerido**: **requerem** força o AirDrop a ser considerado um destino não gerido. Ele impede que as aplicações geridas de enviar dados através de Airdrop. 
- **Adicionar amigos do Game Center (apenas supervisionados)**: **bloco** impede os utilizadores de adição de amigos do Game Center. **Não configurado** permite que o utilizador adicione amigos no Centro de jogos.
- **Centro de jogos (apenas supervisionado)**: **bloco** a utilização da aplicação Game Center. **Não configurado** permite utilizar a aplicação do Centro de jogos no dispositivo.
- **Jogos de multijogadores (apenas supervisionado)**: escolha **bloco** para impedir que os jogos de vários jogadores. **Não configurado** permite que o utilizador Jogue jogos multijogador no dispositivo.
- **Região das classificações**: Escolha a região das classificações que pretende utilizar para transferências permitidas. E, em seguida, selecione as classificações permitidas para **filmes** e **TV mostra**.
- **Aplicações**: selecione a classificação etária permitida das aplicações que os utilizadores podem transferir ou pode escolher **permitir todas as aplicações**.

## <a name="built-in-apps"></a>Aplicações Incorporadas

- **Câmara**: escolha **bloco** para impedir o acesso à câmara do dispositivo. **Não configurado** permite o acesso à câmara do dispositivo.
  - **FaceTime**: **bloco** para impedir o acesso à aplicação FaceTime. **Não configurado** permite o acesso à aplicação FaceTime no dispositivo.
- **Siri**: **bloco** impede o acesso a Siri. **Não configurado** permite usando o Assistente de voz Siri no dispositivo.
  - **Siri enquanto o dispositivo está bloqueado**: escolha **bloco** para impedir o acesso a Siri quando o dispositivo está bloqueado. **Não configurado** permite usando o Assistente de voz Siri no dispositivo quando ele está bloqueado.
  - **Filtro de linguagem inapropriada da Siri (apenas supervisionado)**: **requerem** impede que a Siri Dite ou fale com linguagem profana.
  - **A siri pode consultar conteúdos gerados pelo utilizador da internet (apenas supervisionado)**: **bloco** impede a Siri de aceder ao Web sites para responder a perguntas. **Não configurado** permite que a siri pode aceder a conteúdos gerados pelo utilizador a partir da internet.
- **Apple News (apenas supervisionado)**: escolha **bloco** para impedir o acesso à aplicação Apple News no dispositivo. **Não configurado** permite utilizar a aplicação Apple News.
- **loja iBooks (apenas supervisionada)**: **bloco** impede o acesso à iBooks store. **Não configurado** permite aos utilizadores procurar e compre livros da loja iBooks.
- **Aplicação mensagens no dispositivo (apenas supervisionado)**: escolha **bloco** para que os utilizadores não é possível utilizar a aplicação de mensagens no dispositivo. **Não configurado** permite utilizar a aplicação de mensagens para enviar e ler mensagens de texto.
- **Podcasts (apenas supervisionado)**: **bloco** impede que os utilizadores através da aplicação Podcasts. **Não configurado** permite a utilização da aplicação Podcasts.
- **Serviço Music (apenas supervisionado)**: **bloco** reverte o aplicativo de música para o modo clássico e desativa o serviço de música. **Não configurado** permite o uso de aplicação Apple Music.
- **serviço iTunes Radio (apenas supervisionado)**: **bloco** impede os utilizadores de utilizar a aplicação iTunes Radio. **Não configurado** permite o uso de aplicação iTunes Radio.
- **Alterações às definições da aplicação encontrar amigos (apenas supervisionadas)**: **bloco** impede alterações às definições da aplicação Find My Friends. **Não configurado** permite que o utilizador altere as definições da aplicação Find My Friends.
- **Pesquisa Spotlight para devolver resultados da internet (apenas supervisionado)**: **bloco** impede o destaque do retorno de resultados de uma pesquisa na Internet. **Não configurado** permite destaque pesquisa ligar à Internet para fornecer os resultados da pesquisa.
- **Bloquear a remoção de aplicações do sistema do dispositivo (apenas supervisionado)**: escolha **bloco** desativa a capacidade de remover aplicações de sistema do dispositivo. **Não configurado** permite aos utilizadores remover aplicações do sistema.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- **Aplicações proibidas**: uma lista de aplicações não geridas pelo Intune que não quer instalada no dispositivo. Se um usuário instala uma aplicação a partir desta lista, é notificado pelo Intune.
- **Aplicações aprovadas**: uma lista de aplicações que os utilizadores podem instalar. Para ficar em conformidade, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas. Se um usuário instala uma aplicação a partir desta lista, é notificado pelo Intune.

Adicionar aplicações para estas listas, pode:

- **Adicionar** a aplicação na iTunes store URL da aplicação que pretende. Por exemplo, para adicionar a aplicação pastas de trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Pode também utilizar o iTunes para localizar a aplicação e, em seguida, utilizar o **copiar ligação** tarefa para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o <app url>, <app name>, <app publisher> formato. Em alternativa, exportar uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Perfis de dispositivos que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar ou ocultar aplicações (apenas supervisionado)

Na lista de aplicações Mostrar ou ocultar, pode configurar uma das seguintes listas em dispositivos supervisionados com o iOS 9.3 ou mais recente.

- **Aplicações ocultas**: introduza uma lista de aplicações que estão ocultos dos utilizadores. Os utilizadores não podem ver ou abra estas aplicações.
- **Aplicações visíveis**: introduza uma lista de aplicações que os utilizadores podem ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

Adicionar aplicações para estas listas, pode:

- **Adicionar** a aplicação na iTunes store URL da aplicação que pretende. Por exemplo, para adicionar a aplicação pastas de trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Pode também utilizar o iTunes para localizar a aplicação e, em seguida, utilizar o **copiar ligação** tarefa para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o <app url>, <app name>, <app publisher> formato. Em alternativa, exportar uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

## <a name="wireless"></a>Sem fios

- **Roaming de dados**: escolha **bloco** para impedir que os dados em roaming na rede celular. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **Obtenção de segundo plano global roaming**: **bloco** impede a utilizar a funcionalidade de obtenção de em segundo plano global quando em roaming na rede celular. **Não configurado** permite que o dispositivo obtenha dados, tais como e-mail, quando está em roaming numa rede celular.
- **Marcação por voz**: escolha **bloco** para impedir que os utilizadores a utilizar a funcionalidade de marcação por voz no dispositivo. **Não configurado** permite as chamadas discar no dispositivo.
- **Roaming de voz**: escolha **bloco** para impedir que chamadas em roaming na rede celular. **Não configurado** permite chamadas em roaming quando o dispositivo estiver numa rede celular.
- **Alterações às definições de utilização de dados via rede móvel de aplicação (apenas supervisionadas)**: escolha **bloco** para impedir alterações às definições de utilização de dados via rede móvel da aplicação. **Não configurado** permite que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.
- **Hotspot pessoal**: **bloco** impede que o dispositivo a ser utilizado como um hotspot pessoal. Esta definição poderá não ser compatível com algumas operadoras. **Não configurado** permite esta funcionalidade.
- **Junte-se a redes Wi-Fi apenas com perfis de configuração (apenas supervisionados)**: **requerem** força o dispositivo para utilizar apenas as redes Wi-Fi configuradas através de perfis de configuração do Intune. **Não configurado** permite que o dispositivo utilize outras redes Wi-Fi.
- **Regras de utilização de rede móvel (apenas aplicações geridas)**: definir os dados de tipos de aplicações geridas podem utilizar em redes de celular. As opções são:
  - **Bloquear a utilização de dados via rede móvel**: bloquear dados via rede móvel para a utilizar **todas as aplicações geridas** ou **escolher aplicações específicas**.
  - **Bloquear a utilização de dados via rede móvel ao efetuar o roaming**: bloquear com dados via rede móvel ao efetuar o roaming para **todas as aplicações geridas** ou **escolher aplicações específicas**.

## <a name="connected-devices"></a>Dispositivos Ligados

- **AirDrop (apenas supervisionado)**: **bloco** impede o AirDrop a utilizar no dispositivo. **Não configurado** permite o uso da funcionalidade AirDrop para trocar conteúdos com dispositivos próximos.
- **Emparelhamento do Apple Watch (apenas supervisionado)**: **bloco** impede o emparelhamento com um Apple Watch. **Não configurado** permite que o dispositivo se emparelhe com um Apple Watch.
- **Deteção de pulso para do Apple Watch emparelhado**: **requerem** força um Apple Watch emparelhado a utilizar a deteção de pulso. Quando for necessário, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 
- **Modificação de Bluetooth (apenas supervisionada)**: **bloco** impede o utilizador final a alterar as definições de Bluetooth no dispositivo. **Não configurado** permite ao utilizador alterar estas definições.
- **Alojar o emparelhamento para controlar os dispositivos que um dispositivo iOS pode emparelhar (apenas supervisionado)**: **não configurado** permite o emparelhamento de anfitriões para permitir que o controle de administrador que dispositivos um dispositivo iOS pode emparelhar. **Bloco** impede que o emparelhamento de anfitriões.
- **Exigir palavra-passe de emparelhamento para pedidos de saída do AirPlay**: **requerem** uma palavra-passe emparelhada quando o utilizador utiliza AirPlay transmitir conteúdos para outros dispositivos da Apple. **Não configurado** permite que o usuário transmitir conteúdo com o AirPlay sem introduzir uma palavra-passe.
- **AirPrint de bloco (apenas supervisionado)**: escolha **bloco** para impedir a utilizar a funcionalidade de AirPrint no dispositivo. **Não configurado** permite que o utilizador utilize o AirPrint.
  - **Bloquear o armazenamento de credenciais do AirPrint na Keychain (apenas supervisionado)**: **bloco** impede a utilizar o armazenamento de Keychain para o nome de utilizador e palavra-passe no dispositivo. **Não configurado** permite armazenar o nome de utilizador do AirPrint e a palavra-passe na aplicação Keychain.
  - **Exigir um certificado fidedigno do TLS para AirPrint (apenas supervisionado)**: **requerem** força o dispositivo para utilizar certificados fidedignos para comunicação de impressão de TLS.
  - **Deteção de iBeacon do bloco de impressoras com o AirPrint (apenas supervisionado)**: **bloco** impede maliciosos AirPrint Bluetooth beacons de phishing para tráfego de rede. **Não configurado** permite que o anúncio de impressoras com o AirPrint no dispositivo.

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

- **Pesquisa de definição de palavras (apenas supervisionada)**: **bloco** impede o utilizador de realçar uma palavra e, em seguida, procurar a respetiva definição no dispositivo. **Não configurado** permite o acesso para o recurso de pesquisa de definição.
- **Teclados preditivos (apenas supervisionados)**: **não configurado** permite a utilização de teclados preditivos para sugerem palavras que o utilizador pode desejar. **Bloco** impede que esta funcionalidade.
- **Correção automática (apenas supervisionada)**: **não configurado** permite que o dispositivo corrija automaticamente palavras com erros ortográficos. **Bloco** impede autocorrection a utilizar.
- **(Apenas supervisionada) de verificação ortográfica do teclado**: **não configurado** permite o uso de verificador ortográfico do dispositivo. **Bloco** permite que o verificador ortográfico.
- **(Apenas supervisionados) de atalhos de teclado**: **não configurado** permite o uso de atalhos de teclado no dispositivo. **Bloco** impede o utilizador utilizar atalhos de teclado.
- **Ditado (apenas supervisionado)**: **bloco** impede o utilizador através de entradas de voz para introduzir texto. **Não configurado** permite que o utilizador utilize a entrada de ditado.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Cópia de segurança para iCloud**: **não configurado** permite ao utilizador efetuar cópias de segurança do dispositivo para iCloud. **Bloco** impede o utilizador de cópias de segurança de dispositivo para iCloud.
- **Sincronização de documentos com a iCloud (apenas supervisionado)**: **não configurado** permite a sincronização de documentos e chave-valor para o seu espaço de armazenamento do iCloud. **Bloco** impede a sincronização de documentos e dados de iCloud.
- **Fotografia stream sincronizados com o iCloud**: **não configurado** permite aos utilizadores ativar **minha fotografia Stream** no respetivo dispositivo sincronizadas com o iCloud e ter fotos disponíveis nos dispositivos do utilizador. **Bloco** impede a fotografia stream sincronizados com o iCloud.
- **Cópia de segurança encriptada**: **requerem** para cópias de segurança do dispositivo tem de estar encriptadas.
- **Fototeca em iCloud**: definido como **bloco** para desativar a utilizar a biblioteca de fotografias do iCloud para armazenar fotografias e vídeos na cloud. Qualquer fotos não sido completamente transferidas da Fototeca em iCloud para o dispositivo são removidas do dispositivo. **Não configurado** permite o uso da biblioteca de fotografias do iCloud.
- **Sincronização das aplicações na cloud geridas**: **não configurado** permite que as suas aplicações gere o Intune sincronizem dados para a conta de utilizador iCloud. **Bloco** impede que a sincronização de dados para o iCloud.
- **Transmissão partilhada de fotografias**: escolha **bloco** para desativar **partilha de fotografias do iCloud** no dispositivo. **Não configurado** permite a transmissão em fluxo de fotografias partilhadas.
- **Continuação da atividade**: **não configurado** permite aos utilizadores continuar o trabalho que iniciou num dispositivo iOS noutro dispositivo de iOS ou macOS (Handoff). **Bloco** impede este handoff.
- **Bloquear a sincronização de Keychain do iCloud**: escolha **bloco** para desativar a sincronização credenciais armazenadas na Keychain com o iCloud. **Não configurado** permite que os usuários sincronizar estas credenciais.
- **Cópia de segurança do bloco Enterprise livro**: escolha **bloco** impedir os utilizadores de backup de livros de enterprise. **Não configurado** permite aos utilizadores criar cópias de segurança estes manuais.
- **Bloquear a sincronização de metadados de livro enterprise (notas e destaques)**: **bloco** impede que sincronize notas e destaques em livros do enterprise. **Não configurado** permite que a sincronização.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicação única autónomo (apenas supervisionado)

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo está bloqueado. Só pode ser executado essa aplicação. Por exemplo, adicione uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

Adicionar aplicações, pode:

- Introduza o **nome da aplicação** e **ID do pacote de aplicação**e selecione **Add**. [Referência de ID para aplicações iOS incorporadas do pacote](#bundle-id-reference-for-built-in-ios-apps) (Este artigo) inclui algumas aplicações com suas IDs.
- **Importar** um ficheiro CSV com a lista de nomes de aplicações e os IDs de coleção. Ou, **exportar** uma lista existente, que inclui as aplicações.

## <a name="kiosk-supervised-only"></a>Quiosque (apenas supervisionado)

- **Aplicação seja executada no modo de quiosque**: Escolha o tipo de aplicações que pretende executar no modo de local público. As opções são: 
  - **Aplicação de Store**: introduza o URL para uma aplicação na App store do iTunes
  - **Aplicação gerida**: escolher uma aplicação que adicionar ao Intune
  - **Aplicação incorporada**: introduza o [ID de pacote](#bundle-id-reference-for-built-in-ios-apps) da aplicação incorporada

- **Toque de apoio**: **requerem** a definição de acessibilidade Assistivetouch estar no dispositivo. Esta funcionalidade ajuda os utilizadores na tela gestos, que podem ser difícil para eles. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Inverter cores**: **requerem** a definição de acessibilidade de inverter cores para os utilizadores com deficiências visuais possam alterar a tela de apresentação. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Áudio mono**: **requerem** a definição de acessibilidade áudio Mono estar no dispositivo. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **VoiceOver**: **requerem** a definição de acessibilidade de VoiceOver ser no dispositivo para a leitura em voz alta o texto na tela. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Zoom**: **requerem** a definição de Zoom de ser no dispositivo para permitir que os utilizadores a utilizar o toque para aumentar o zoom no ecrã. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Bloqueio automático**: **permitir** bloqueio automático do dispositivo. **Não configurado** desativa esta funcionalidade.
- **Comutador do toque**: **permitir** mudar da alteração do toque (desativar som) no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Rotação do ecrã**: **permitir** mudança da orientação do ecrã quando o utilizador roda o dispositivo. **Não configurado** desativa esta funcionalidade.
- **Botão de suspensão do ecrã**: escolha **permitir** para desativar o botão de reativação de suspensão do ecrã no dispositivo. **Não configurado** habilita esse recurso.
- **Touch**: **bloco** desativa o ecrã tátil do dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **permitir** utilizando os botões de volume no dispositivo. **Não configurado** desativa os botões de volume.
- **Controlo tátil de apoio**: **permitir** permitem que os utilizadores utilizem a função assistivetouch. **Não configurado** desativa esta funcionalidade.
- **Controlo de cores de inversão**: **permitir** inverter ajustes para permitir aos utilizadores ajustar a função Inverter cores de cores. **Não configurado** desativa esta funcionalidade.
- **Falar em texto selecionado**: **permitir** as definições de acessibilidade enunciar seleção estar no dispositivo. Esta funcionalidade lê o texto que o utilizador seleciona em voz alta. **Não configurado** desativa esta funcionalidade.
- **Controlo de voiceOver**: **permitir** alterações voiceover para permitir aos utilizadores atualizar a função VoiceOver, por exemplo, a rapidez na tela de leitura do texto em voz alta. **Não configurado** impede alterações voiceover.
- **Controlo de zoom**: **permitir** zoom alterações pelo utilizador. **Não configurado** impede alterações de zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre como utilizar a ferramenta Apple Configurator.
> Se a aplicação iOS a que introduzir estiver instalada depois de atribuir o perfil, em seguida, o dispositivo não introduza o modo de local público até que o dispositivo é reiniciado.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referência de ID do pacote para aplicações iOS incorporadas

Esta lista mostra o ID do pacote de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software.

| ID do Pacote                   | Nome da Aplicação     | Publisher |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendário     | Apple     |
| com.apple.camera            | Câmara       | Apple     |
| com.apple.mobiletimer       | Relógio        | Apple     |
| com.apple.compass           | Bússola      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.mobileme.fmf1     | Encontrar Amigos | Apple     |
| com.apple.mobileme.fmip1    | Localizar iPhone  | Apple     |
| com.apple.gamecenter        | Centro de Jogos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Estado de Funcionamento       | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Correio         | Apple     |
| com.apple.Maps              | Mapas         | Apple     |
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
| com.apple.MobileSafari      | Safari       | Apple     |
| com.apple.Preferences       | Definições     | Apple     |
| com.apple.stocks            | Bolsa       | Apple     |
| com.apple.tips              | Sugestões         | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Meteorologia      | Apple     |

## <a name="safari"></a>Safari

- **Safari (apenas supervisionado)**: **bloco** utilização do browser Safari no dispositivo. **Não configurado** permite que os utilizadores a utilizar o browser Safari.
- **Preenchimento automático**: **bloco** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** permite que os utilizadores alterem as definições do browser.
- **Cookies**: Escolha a forma como os cookies são processados no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **JavaScript**: **bloco** impede que os scripts em Java no browser em execução no dispositivo. **Não configurado** permite que os scripts de Java.
- **Avisos de fraude**: **requerem** avisos de fraude para ser mostrada no navegador da web no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Pop-ups**: **bloco** para desativar o Bloqueador de pop-up no browser. **Não configurado** permite que o Bloqueador de pop-up.

## <a name="domains"></a>Domínios

### <a name="unmarked-email-domains"></a>Domínios de e-mail não marcados

Na **URL de domínio de E-Mail**, adicione um ou mais URLs à lista. Quando os utilizadores finais recebem um e-mail de um domínio não os domínios que introduzir, o e-mail é marcado como não fidedigno na aplicação Mail do iOS.

### <a name="managed-web-domains"></a>Domínios Web geridos

Na **URL de domínio do Web**, adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzir, que sejam considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

### <a name="safari-password-autofill-domains"></a>Domínios de preenchimento automático de palavras-passe do Safari

Na **URL de domínio**, adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Esta definição aplica-se apenas ao browser Safari e aos dispositivos iOS 9.3 e posterior no modo supervisionado. Se não especificar nenhum URL, as palavras-passe poderão ser guardadas a partir de todos os sites.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md) seu status.
