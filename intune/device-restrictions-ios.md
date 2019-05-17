---
title: Definições dos dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos iOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilizar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, gerir dispositivos Bluetooth, ligar à cloud para cópia de segurança e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o browser Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/02/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d0623e9d12132ac470813d65510bc2c76379109
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898637"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições dos dispositivos iOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar nos dispositivos iOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Partilhar dados de utilização**: escolha **Bloquear** para impedir que o dispositivo envie dados de diagnóstico e de utilização à Apple. **Não configurado** (predefinição) permite que estes dados sejam enviados.
  - **Modificação das definições da submissão de diagnósticos (apenas supervisionado)**: **Bloquear** impede que o utilizador altere as definições da análise da aplicação e da submissão de diagnóstico em **Diagnóstico e Utilização** (Definições do dispositivo). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

    Esta funcionalidade aplica-se a:  
    - iOS 9.3.2 e posterior

- **Captura de ecrã**: escolha **Bloquear** para impedir as capturas de ecrã no dispositivo. No iOS 9.0 e posterior, também inclui bloquear as gravações de ecrãs. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.
  - **Observação remota do ecrã através da aplicação Classroom (apenas supervisionado)**: escolha **Bloquear** para impedir que a aplicação Classroom veja remotamente o ecrã no dispositivo. **Não configurado** (predefinição) permite que a aplicação Classroom da Apple veja o ecrã.

    Esta funcionalidade aplica-se a:  
    - iOS 9.3 e posterior

  - **Observação não solicitada do ecrã através da aplicação Classroom (apenas supervisionado)**: se definido como **Permitir**, os professores podem observar o ecrã dos dispositivos iOS dos estudantes de forma silenciosa através da aplicação Classroom sem o conhecimento dos estudantes. Os dispositivos de estudantes inscritos numa turma através da aplicação Classroom concedem automaticamente permissão ao professor do curso. **Não configurado** (predefinição) impede esta funcionalidade.
- **Certificados TLS não fidedignos**: escolha **Bloquear** para impedir os certificados Transport Layer Security (TLS) não fidedignos no dispositivo. **Não configurado** (predefinição) permite os certificados TLS.
- **Confiança das aplicações empresariais**: escolha **Bloquear** para remover o botão **Confiar no Programador Empresarial** em Definições > Geral > Perfis e Gestão de Dispositivos no dispositivo. **Não configurado** (predefinição) permite que o utilizador opte por confiar nas aplicações que não são transferidas da App Store.
- **Modificação da conta (apenas supervisionado)**: quando definido como **Bloquear**, o utilizador não pode atualizar as definições específicas do dispositivo na aplicação de definições do iOS. Por exemplo, o utilizador não pode criar contas novas no dispositivo nem alterar o nome de utilizador ou a palavra-passe. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade também se aplica às definições acessíveis na aplicação de definições do iOS, tais como o Correio, Contactos, Calendário, Twitter e outros. A funcionalidade não se aplica a aplicações com definições da conta que não sejam configuráveis na aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.
- **Tempo do ecrã (apenas supervisionado)**: escolha **Bloquear** para impedir que os utilizadores definam as suas próprias restrições em Tempo do Ecrã (definições do dispositivo). **Não configurado** permite que o utilizador configure as restrições do dispositivo (por exemplo, as restrições de acesso ou as restrições de conteúdo e de privacidade) no dispositivo.

  O nome desta definição foi mudado em **Ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 e anterior: **Bloquear** impede que os utilizadores finais definam as suas próprias restrições nas definições do dispositivo. Esta é a mesma definição; e não qualquer alteração para os utilizadores finais.
  - iOS 12.0 e posterior: **Bloquear** impede que os utilizadores finais definam o seu próprio **Tempo do Ecrã** nas definições do dispositivo (Definições > Geral > Tempo do Ecrã), incluindo as restrições de conteúdo e de privacidade. Os dispositivos atualizados para o iOS 12.0 deixam apresentar o separador de restrições nas definições do dispositivo (Definições > Geral > Gestão de Dispositivos > Perfil de Gestão > Restrições). Estas definições estão em **Tempo do Ecrã**.
  
- **Utilização da opção Apagar todos os conteúdos e definições no dispositivo (apenas supervisionado)**: escolha **Bloquear** para que os utilizadores não possam utilizar a opção Apagar todos os conteúdos e definições no dispositivo (apenas supervisionado). **Não configurado** (predefinição) concede aos utilizadores acesso a estas definições.
- **Modificação do nome do dispositivo (apenas supervisionado)**: escolha **Bloquear** para que não seja possível alterar o nome do dispositivo. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Modificação das definições de notificação (apenas supervisionado)**: escolha **Bloquear** para que não seja possível alterar as definições de notificação. **Não configurado** (predefinição) permite ao utilizador alterar as definições de notificação do dispositivo.
- **Modificação da imagem de fundo (apenas supervisionado)**: **Bloquear** impede que a imagem de fundo seja alterada. **Não configurado** (predefinição) permite ao utilizador alterar a imagem de fundo no dispositivo.
- **Modificação das definições de confiança das aplicações empresariais (apenas supervisionado)**: **Bloquear** impede que o utilizador altere as definições de confiança das aplicações empresariais nos dispositivos supervisionados. **Não configurado** (predefinição) permite que o utilizador confie nas aplicações que não são transferidas da App Store.
- **Alterações do perfil de configuração (apenas supervisionado)**: **Bloquear** impede que o perfil de configuração seja alterado no dispositivo. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Bloqueio de Ativação (apenas supervisionado)**: escolha **Permitir** para ativar o Bloqueio de Ativação nos dispositivos iOS supervisionados. O Bloqueio de Ativação dificulta que um dispositivo perdido ou roubado seja reativado.
- **Bloquear a remoção de aplicações (apenas supervisionado)**: escolha **Bloquear** para impedir que os utilizadores removam aplicações. **Não configurado** (predefinição) permite que os utilizadores removam aplicações do dispositivo.
- **Bloqueia o modo USB Restrito (apenas supervisionado)**: escolha **Bloquear** para desativar o modo USB Restrito nos dispositivos supervisionados. O modo USB Restrito bloqueia a troca de dados de acessórios USB com um dispositivo que está bloqueado há mais de uma hora. **Não configurado** (predefinição) permite o modo USB Restrito.
- **Forçar a automatização da data e da hora (apenas supervisionado)**: **Exigir** força os dispositivos supervisionados a definir automaticamente a Data e a Hora. O fuso horário do dispositivo é atualizado quando o dispositivo está ligado à rede móvel ou ao Wi-Fi com os serviços de localização ativados.
- **Exigir que os estudantes solicitem permissão para sair do curso do Classroom (apenas supervisionado)**: **Exigir** força os estudantes inscritos num curso não gerido através do Classroom a pedir permissão ao professor para saírem do curso. **Não configurado** (predefinição) não força o estudante a pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11.3 e posterior

- **Permitir ao Classroom bloquear uma aplicação e bloquear o dispositivo sem pedir (apenas supervisionado)**: **Ativar** permite que o professor bloqueie aplicações ou bloqueie o dispositivo através da aplicação Classroom sem avisar o estudante. Bloquear aplicações significa que o dispositivo pode apenas aceder às aplicações especificadas pelo professor. **Não configurado** (predefinição) impede que os professores bloqueiem aplicações ou dispositivos através da aplicação Classroom sem avisar o estudante. 

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Aderir automaticamente a turmas do Classroom sem pedir (apenas supervisionado)**: **Ativar** permite automaticamente que os estudantes adiram a uma turma da aplicação Classroom sem pedir ao professor. **Não configurado** (predefinição) aviso o professor que os estudantes querem aderir a uma turma da aplicação Classroom.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Permitir atualizações PKI por ondas eletromagnéticas**: **Permitir** deixa que os utilizadores recebam atualizações de software sem precisarem de ligar os dispositivos a um computador.
- **Limitar rastreio de anúncios**: escolha **Limitar** para desativar o identificador de publicidade do dispositivo. **Não configurado** (predefinição) mantém-no ativado.
- **Bloquear criação de VPN (apenas supervisionado)**: **Bloquear** impede que os utilizadores criem definições de configuração de VPN. **Não configurado** (predefinição) deixa que os utilizadores criem VPNs no dispositivo.
- **Modificar definições de eSIM (apenas supervisionado)**: **Bloquear** impede que os utilizadores removam ou adicionem um plano da rede móvel ao eSIM no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12.1 e posterior

- **Adiar atualizações de software (apenas supervisionado)**: quando definido como **Não configurado** (predefinição), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização do iOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar visibilidade das atualizações de software**: introduza um valor entre 0 e 90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se iOS 12.a estiver disponível a **1 de janeiro** e a opção **Adiar visibilidade** estiver definida como **5 dias**, a iOS 12.a não será mostrado como uma atualização disponível nos dispositivos do utilizador final. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta definição aplica-se a:  
    - iOS 11.3 e posterior

## <a name="password"></a>Palavra-passe

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** permite que os utilizadores acedam ao dispositivo sem introduzir uma palavra-passe.
  - **Palavras-passe simples**: escolha **Bloquear** para exigir palavras-passe mais complexas. **Não configurado** permite palavras-passe simples, tais como `0000` e `1234`.
  - **Tipo obrigatório de palavra-passe**: escolha o tipo de palavra-passe exigido pela sua organização. As opções são:
    - **Predefinição do dispositivo**
    - **Numérico**
    - **Alfanumérico**
  - **Número de carateres não alfanuméricos na palavra-passe**: especifique o número de caracteres de símbolos, tais como `#` ou `@`, que têm de ser incluídos na palavra-passe.
  - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo que um utilizador tem de introduzir (entre 4 e 14 carateres).
  - **Número de falhas de início de sessão antes de apagar o dispositivo**: introduza o número de inícios de sessão falhados permitidos antes de o dispositivo ser apagado (entre 1 e 11).
  - **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**<sup>1</sup>: introduza o período de tempo durante o qual o dispositivo permanece inativo antes de o utilizador ter de reintroduzir a palavra-passe. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Suportado no iOS 8.0 e em dispositivos mais recentes.
  - **Máximo de minutos de inatividade até o ecrã ser bloqueado**<sup>1</sup>: introduza o número máximo de minutos de inatividade permitidos no dispositivo até o ecrã bloquear. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido.
  - **Expiração da palavra-passe (dias)**: introduza o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.
  - **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas para que uma palavra-passe antiga possa ser reutilizada.
  - **Desbloqueio por impressão digital**: escolha **Bloquear** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Modificação do código de acesso (apenas supervisionado)**: escolha **Bloquear** para impedir que o código de acesso seja alterado, adicionado ou removido. As alterações às restrições do código de acesso são ignoradas nos dispositivos supervisionados após o bloqueio desta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.

  - **Modificação da impressão digital (apenas supervisionado)**: **Bloquear** impede o utilizador de alterar, adicionar ou remover impressões digitais TouchID. **Não configurado** (predefinição) permite que o utilizador atualize as impressões digitais TouchID no dispositivo.

- **Bloquear Preenchimento Automático de palavras-passe (apenas supervisionado)**: escolha **Bloquear** para impedir a utilização da funcionalidade Preenchimento Automático de Palavras-passe no iOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear pedidos de proximidade de palavra-passe (apenas supervisionado)**: escolha **Bloquear** para que o dispositivo de um utilizador não peça palavras-passe aos dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.
- **Bloquear partilha de palavras-passe (apenas supervisionado)**: **Bloquear** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.
- **Exigir a autenticação por Touch ID ou Face ID para Preenchimento Automático de palavra-passes ou informações de cartão de crédito (apenas supervisionado)**: quando definido como **Exigir**, os utilizadores têm de se autenticar com o Touch ID ou o Face ID para que as palavras-passe ou as informações de cartão de crédito possam ser preenchidas automaticamente no Safari e noutras aplicações. **Não configurado** (predefinição) permite que os utilizadores controlem esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor de ambas as definições para **5** minutos, o ecrã desativa automaticamente passados cinco minutos e o dispositivo bloqueia após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, após o utilizador desativar o ecrã, o dispositivo será bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

- **Acesso ao Centro de Controlo enquanto o dispositivo está bloqueado**: escolha **Bloquear** para impedir o acesso à aplicação do Centro de Controlo enquanto o dispositivo está bloqueado. **Não configurado** permite que o utilizador aceda à aplicação do Centro de Controlo quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso às notificações quando o dispositivo está bloqueado. **Não configurado** permite que o utilizador aceda às notificações sem desbloquear o dispositivo.
- **Notificações da Carteira enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso à aplicação Carteira quando o dispositivo está bloqueado. **Não configurado** permite que o utilizador aceda à aplicação Carteira enquanto o dispositivo está bloqueado.
- **Vista Hoje enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso à vista Hoje enquanto o dispositivo está bloqueado. **Não configurado** permite que o utilizador veja a vista Hoje enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

- **App Store**: **Bloquear** impede o acesso à App Store em dispositivos supervisionados. **Não configurado** permite o acesso.
  - **Instalar aplicações a partir da App Store (apenas supervisionado)**: escolha **Bloquear** para bloquear a App Store no ecrã inicial do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** permite a App Store no ecrã inicial.
  - **Transferências automáticas de aplicações (apenas supervisionado)**: escolha **Bloquear** para impedir a transferência automática de aplicações compradas noutros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** permite que as aplicações compradas noutros dispositivos iOS sejam transferidas no dispositivo.
- **Palavra-passe para aceder à App Store**: **Exigir** ao utilizador que introduza uma palavra-passe para poder visitar a App Store. **Não configurado** permite o acesso à App Store sem introduzir uma palavra-passe.
- **Compras na aplicação**: escolha **Bloquear** para impedir compras na aplicação na loja. **Não configurado** permite as compras na loja numa aplicação em execução.
- **Conteúdo explícito de música, podcasts ou notícias no iTunes (apenas supervisionado)**: escolha **Bloquear** para impedir música, podcasts ou notícias de conteúdo explícito no iTunes. **Não configurado** permite que o dispositivo aceda a conteúdo da loja classificado como conteúdo para adultos.
- **Transferir conteúdos da iBooks Store sinalizados como “Erótico”**: Escolha **Bloquear** para impedir que os utilizadores transfiram multimédia da iBook Store marcado como “erótico”. **Não configurado** permite que o utilizador transfira livros da categoria “Erotismo”.
- **Ver documentos empresariais em aplicações não geridas**: **Bloquear** impede a visualização de documentos empresariais em aplicações não geridas. **Não configurado** permite que os documentos empresariais sejam visualizados em qualquer aplicação. Por exemplo, quer impedir que os utilizadores guardem os ficheiros da aplicação OneDrive na Dropbox. Configure esta definição como **Bloquear**. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não é permitido guardar.
  - **Permitir que aplicações geridas escrevam contactos em contas não geridas**: quando definido como **Permitir**, os utilizadores podem adicionar ou sincronizar informações de contacto do Outlook de qualquer pessoa, incluindo contactos de negócios e da empresa, para a aplicação Contactos incorporada no dispositivo. Quando definido como **Não configurado**, os utilizadores não podem adicionar contatos do Outlook à aplicação Contactos incorporada no dispositivo.
  
    Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.
  
- **Ver documentos não empresariais em aplicações empresariais**: **Bloquear** impede a visualização de documentos não empresariais nas aplicações da empresa. **Não configurado** permite que qualquer documento seja visualizado nas aplicações geridas da empresa.
  - **Permitir que aplicações não geridas leiam a partir de contas com contactos geridas**: quando definido como **Permitir**, os utilizadores podem adicionar informações de contato da aplicação iContacts de qualquer pessoa ao Outlook. **Não configurado** impede a leitura, incluindo a remoção de duplicados, na aplicação Contactos incorporada no dispositivo.
  
    Para utilizar esta definição, configure **Ver documentos não empresariais em aplicações empresariais** como **Bloquear**.
  
- **Tratar o AirDrop como um destino não gerido**: **Exigir** força o AirDrop a ser considerado como um destino não gerido. Impede que as aplicações geridas enviem dados através do Airdrop. 
- **Adicionar amigos do Game Center (apenas supervisionado)**: **Bloquear** impede que os utilizadores adicionem amigos do Game Center. **Não configurado** permite que o utilizador adicione amigos no Game Center.
- **Game Center (apenas supervisionado)**: **Bloquear** a utilização da aplicação Game Center. **Não configurado** permite a utilização da aplicação Game Center no dispositivo.
- **Jogos de vários jogadores (apenas supervisionado)**: escolha **Bloquear** para impedir jogos de vários jogadores. **Não configurado** permite que o utilizador jogue jogos com vários jogadores no dispositivo.
- **Região das classificações**: escolha a região das classificações que quer utilizar para as transferências permitidas. E, em seguida, escolha as classificações permitidas para **Filmes** e **Programas de TV**.
- **Aplicações**: escolha a classificação etária permitida para as aplicações que os utilizadores podem transferir ou pode optar por **Permitir Todas as Aplicações**.

## <a name="built-in-apps"></a>Aplicações Incorporadas

- **Câmara**: escolha **Bloquear** para impedir o acesso à câmara no dispositivo. **Não configurado** permite o acesso à câmara do dispositivo.
  - **FaceTime**: **Bloquear** para impedir o acesso à aplicação FaceTime. **Não configurado** permite o acesso à aplicação FaceTime no dispositivo.
- **Siri**: **Bloquear** impede o acesso à Siri. **Não configurado** permite utilizar a assistente de voz Siri no dispositivo.
  - **Siri enquanto o dispositivo está bloqueado**: escolha **Bloquear** para impedir o acesso à Siri enquanto o dispositivo está bloqueado. **Não configurado** permite utilizar a assistente de voz Siri no dispositivo quando está bloqueado.
  - **Filtro de palavras ofensivas da Siri (apenas supervisionado)**: **Exigir** impede a Siri de ditar ou dizer palavras ofensivas.
  - **Siri para consultar conteúdo gerado pelo utilizador a partir da Internet (apenas supervisionado)**: **Bloquear** impede a Siri de aceder a sites para responder a perguntas. **Não configurado** permite à Siri aceder a conteúdos gerados pelo utilizador a partir da Internet.
- **Apple News (apenas supervisionado)**: escolha **Bloquear** para impedir o acesso à aplicação Apple News no dispositivo. **Não configurado** permite utilizar a aplicação Apple News.
- **iBooks Store (apenas supervisionado)**: **Bloquear** impede o acesso à iBooks Store. **Não configurado** permite que os utilizadores procurem e comprem livros na iBooks Store.
- **Aplicação Mensagens no dispositivo (apenas supervisionado)**: escolha **Bloquear** para que os utilizadores não possam utilizar a aplicação Mensagens no dispositivo. **Não configurado** permite utilizar a aplicação Mensagens para ler e enviar mensagens de texto.
- **Podcasts (apenas supervisionado)**: **Bloquear** impede que os utilizadores utilizem a aplicação Podcasts. **Não configurado** permite utilizar a aplicação Podcasts.
- **Serviço Music (apenas supervisionado)**: **Bloquear** reverte a aplicação Music para o modo clássico e desativa o Serviço Music. **Não configurado** permite utilizar a aplicação Apple Music.
- **Serviço iTunes Radio (apenas supervisionado)**: **Bloquear** impede que os utilizadores utilizem a aplicação iTunes Radio. **Não configurado** permite utilizar a aplicação iTunes Radio.
- **Alterações às definições da aplicação Encontrar Amigos (apenas supervisionado)**: **Bloquear** impede alterações às definições da aplicação Encontrar Amigos. **Não configurado** permite que o utilizador altere as definições da aplicação Encontrar Amigos.
- **Pesquisa Spotlight para devolver resultados da Internet (apenas supervisionado)**: **Bloquear** impede a pesquisa Spotlight de devolver resultados de uma pesquisa da Internet. **Não configurado** (predefinição) permite que a pesquisa Spotlight se ligue à Internet para fornecer resultados da pesquisa.
- **Bloquear a remoção de aplicações de sistema do dispositivo (apenas supervisionado)**: escolher **Bloquear** desativa a capacidade de remoção de aplicações de sistema do dispositivo. **Não configurado** permite que os utilizadores removam aplicações de sistema.

#### <a name="safari"></a>Safari

- **Safari (apenas supervisionado)**: **Bloquear** impede a utilização do browser Safari no dispositivo. **Não configurado** permite que os utilizadores utilizem o browser Safari.
- **Preenchimento automático**: **Bloquear** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** permite que os utilizadores alterem as definições de preenchimento automático no browser.
- **Cookies**: escolha a forma como os cookies são processados no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **JavaScript**: **Bloquear** impede que os scripts Java no browser sejam executados no dispositivo. **Não configurado** permite scripts Java.
- **Avisos de fraude**: **Exigir** para que os avisos de fraude sejam mostrados no browser no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Pop-ups**: **Bloquear** para desativar o bloqueador de janelas de pop-up no browser. **Não configurado** permite o bloqueador de janelas de pop-up.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- **Aplicações proibidas**: uma lista de aplicações não geridas pelo Intune que não quer que sejam instaladas no dispositivo. Se um utilizador instalar uma aplicação desta lista, receberá uma notificação do Intune.
- **Aplicações aprovadas**: uma lista de aplicações que os utilizadores têm permissão para instalar. Para permanecerem compatíveis, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas. Se um utilizador instalar uma aplicação desta lista, receberá uma notificação do Intune.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. Por exemplo, para adicionar a aplicação Pastas de Trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Em alternativa, exporte uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar ou ocultar aplicações (apenas supervisionado)

Na lista Mostrar ou ocultar aplicações, pode configurar uma das seguintes listas nos dispositivos supervisionados com o iOS 9.3 ou mais recente.

- **Aplicações ocultas**: introduza uma lista de aplicações que são ocultadas dos utilizadores. Os utilizadores não podem ver nem abrir estas aplicações.
- **Aplicações visíveis**: introduza uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. Por exemplo, para adicionar a aplicação Pastas de Trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Em alternativa, exporte uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

## <a name="wireless"></a>Sem fios

- **Roaming de dados**: escolha **Bloquear** para impedir o roaming de dados na rede móvel. **Não configurado** (predefinição) permite o roaming de dados quando o dispositivo está numa rede móvel.
- **Obtenção global em segundo plano em roaming**: **Bloquear** impede que seja utilizada a funcionalidade de obtenção global em segundo plano quando estiver a utilizar o roaming na rede móvel. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, como o e-mail, quando estiver a utilizar o roaming numa rede móvel.
- **Marcação por voz**: escolha **Bloquear** para impedir que os utilizadores utilizem a funcionalidade de marcação por voz no dispositivo. **Não configurado** (predefinição) permite a marcação por voz no dispositivo.
- **Chamadas em roaming**: escolha **Bloquear** para impedir as chamadas em roaming na rede móvel. **Não configurado** (predefinição) permite as chamadas em roaming quando o dispositivo está numa rede móvel.
- **Alterações às definições de utilização dos dados via rede móvel da aplicação (apenas supervisionado)**: escolha **Bloquear** para impedir as alterações às definições de utilização dos dados via rede móvel da aplicação. **Não configurado** (predefinição) permite que o utilizador controle quais aplicações podem utilizar os dados via rede móvel.
- **Alterações às definições do plano de dados móveis (apenas supervisionadas)**: **Bloquear** impede que os utilizadores alterem qualquer definição no plano de dados móveis. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Hotspot Pessoal**: **Bloquear** desativa o hotspot pessoal no dispositivo dos utilizadores em cada sincronização do dispositivo. Esta definição poderá não ser compatível com algumas operadoras. **Não configurado** (predefinição) mantém a configuração do hotspot pessoal como o conjunto predefinido pelo utilizador.
- **Aderir a redes Wi-Fi apenas com perfis de configuração (apenas supervisionado)**: **Exigir** força o dispositivo a utilizar apenas as redes Wi-Fi configuradas através de perfis de configuração do Intune. **Não configurado** (predefinição) permite que o dispositivo utilize outras redes Wi-Fi.
- **Regras de utilização de rede móvel (apenas aplicações geridas)**: defina os tipos de dados que as aplicações geridas podem utilizar nas redes móveis. As opções são:
  - **Bloquear a utilização de dados via rede móvel**: bloqueie a utilização de dados via rede móvel para **Todas as aplicações geridas** ou opte por **Escolher aplicações específicas**.
  - **Bloquear a utilização de dados via rede móvel ao efetuar o roaming**: bloqueie a utilização de dados via rede móvel ao utilizar o roaming para **Todas as aplicações geridas** ou opte por **Escolher aplicações específicas**.

## <a name="connected-devices"></a>Dispositivos Ligados

- **AirDrop (apenas supervisionado)**: **Bloquear** impede que o AirDrop seja utilizado no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Emparelhamento com Apple Watch (apenas supervisionado)**: **Bloquear** impede o emparelhamento com um Apple Watch. **Não configurado** (predefinição) permite que o dispositivo seja emparelhado com um Apple Watch.
- **Deteção de pulso para Apple Watch emparelhados**: **Exigir** força um Apple Watch emparelhado a utilizar a deteção de pulso. Quando exigido, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 
- **Modificação de Bluetooth (apenas supervisionado)**: **Bloquear** impede que o utilizador final altere as definições de Bluetooth no dispositivo. **Não configurado** (predefinição) permite que o utilizador altere estas definições.
- **Emparelhamento de anfitriões para controlar os dispositivos com que um dispositivo iOS se pode emparelhar (apenas supervisionado)**: **Não configurado** (predefinição) permite o emparelhamento de anfitriões para permitir ao administrador controlar os dispositivos com os quais um dispositivo iOS se pode emparelhar. **Bloquear** impede o emparelhamento de anfitriões.
- **Pedir palavra-passe de emparelhamento para pedidos de saída do AirPlay**: **Exigir** uma palavra-passe de emparelhamento quando o utilizador utiliza o AirPlay para transmitir conteúdo para outros dispositivos da Apple. **Não configurado** (predefinição) permite que o utilizador transmita conteúdo através do AirPlay sem introduzir uma palavra-passe.
- **Bloquear o AirPrint (apenas supervisionado)**: escolha **Bloquear** para impedir a utilização da funcionalidade AirPrint no dispositivo. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Bloquear o armazenamento de credenciais do AirPrint no Keychain (apenas supervisionado)**: **Bloquear** impede a utilização do armazenamento Keychain para o nome de utilizador e a palavra-passe no dispositivo. **Não configurado** (predefinição) permite o armazenamento do nome de utilizador e da palavra-passe do AirPrint na aplicação Keychain.
  - **Requerer um certificado TLS fidedigno para o AirPrint (apenas supervisionado)**: **Exigir** força o dispositivo a utilizar certificados fidedignos para a comunicação de impressão TLS.
  - **Bloquear deteção de iBeacon das impressoras AirPrint (apenas supervisionado)**: **Bloquear** impede que os beacons Bluetooth maliciosos do AirPrint usem phishing no tráfego da rede. **Não configurado** (predefinição) permite a publicidade de impressoras AirPrint no dispositivo.
- **Bloquear a configuração de novos dispositivos próximos (apenas supervisionado)**: **Bloquear** desativa o aviso para configurar novos dispositivos nas proximidades. **Não configurado** (predefinição) permite apresentar avisos aos utilizadores para se ligarem a outros dispositivos Apple próximos.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

- **Pesquisa de definição de palavras (apenas supervisionado)**: **Bloquear** impede que o utilizador realce uma palavra e, em seguida, procure a sua definição no dispositivo. **Não configurado** permite o acesso à funcionalidade de pesquisa de definição.
- **Teclados preditivos (apenas supervisionado)**: **Não configurado** permite utilizar teclados preditivos para sugerir palavras que o utilizador poderá querer introduzir. **Bloquear** impede esta funcionalidade.
- **Correção automática (apenas supervisionado)**: **Não configurado** permite que o dispositivo corrija automaticamente as palavras com erros ortográficos. **Bloquear** impede a utilização da correção automática.
- **Verificação ortográfica do teclado (apenas supervisionado)**: **Não configurado** permite utilizar a verificação ortográfica no dispositivo. **Bloquear** não permite a verificação ortográfica.
- **Atalhos de teclado (apenas supervisionado)**: **Não configurado** permite utilizar os atalhos de teclado no dispositivo. **Bloco** impede o utilizador de utilizar os atalhos de teclado.
- **Ditado (apenas supervisionado)**: **Bloquear** impede o utilizador de utilizar entradas de voz para introduzir texto. **Não configurado** permite que o utilizador utilize a entrada de ditado.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Criar cópias de segurança no iCloud**: **Não configurado** permite que o utilizador faça cópias de segurança do dispositivo para o iCloud. **Bloquear** impede que o utilizador faça cópias de segurança do dispositivo para o iCloud.
- **Bloquear a sincronização de Documentos com o iCloud (apenas supervisionado)**: **Não configurado** permite a sincronização de documentos e de chaves-valor com o espaço de armazenamento do iCloud. **Bloquear** impede o iCloud de sincronizar documentos e dados.
- **Sincronização do fluxo de fotografias com o iCloud**: **Não configurado** permite aos utilizadores ativar **O Meu Fluxo de Fotografias** no dispositivo para sincronizarem com o iCloud e ter as fotografias disponibilizadas em todos os dispositivos do utilizador. **Bloquear** impede a sincronização do fluxo de fotografias com o iCloud.
- **Cópia de segurança encriptada**: **Exigir** para que qualquer cópia de segurança seja encriptada.
- **Fototeca em iCloud**: defina como **Bloquear** para desativar a utilização da fototeca em iCloud para armazenar fotografias e vídeos na cloud. Todas as fotografias que não tiverem sido completamente transferidas da Fototeca em iCloud para o dispositivo serão removidas do dispositivo. **Não configurado** permite utilizar a fototeca em iCloud.
- **Sincronização das aplicações geridas com a cloud** : **Não configurado** permite que as aplicações geridas pelo Intune sincronizem dados com a conta do iCloud do utilizador. **Bloquear** impede esta sincronização de dados com o iCloud.
- **Fluxo partilhado de fotografias**: escolha **Bloquear** para desativar a **Partilha de Fotografias do iCloud** no dispositivo. **Não configurado** permite o fluxo partilhado de fotografias.
- **Continuação da atividade**: **Não configurado** permite aos utilizadores continuarem o trabalho que iniciaram num dispositivo iOS noutro dispositivo iOS ou macOS (Passagem de informações). **Bloquear** impede esta passagem de informações.
- **Bloquear sincronização do Keychain com o iCloud**: escolha **Bloquear** para desativar a sincronização das credenciais armazenadas no Keychain com o iCloud. **Não configurado** permite que os utilizadores sincronizem estas credenciais.
- **Bloquear Cópias de Segurança dos Livros da Empresa**: escolha **Bloquear** para impedir que os utilizadores façam cópias de segurança dos livros da empresa. **Não configurado** permite que os utilizadores façam cópias de segurança destes livros.
- **Bloquear a sincronização de metadados dos livros da empresa (notas e destaques)**: **Bloquear** impede a sincronização das notas e dos destaques dos livros da empresa. **Não configurado** permite a sincronização.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicação única autónomo (apenas supervisionado)

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado. Pode executar apenas essa aplicação. Por exemplo, adicione uma aplicação que permita que os utilizadores façam um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

Para adicionar aplicações, pode:

- Introduzir o **Nome da aplicação** e **ID do Pacote da Aplicação** e selecionar **Adicionar**. A secção [IDs dos pacotes das aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (neste artigo) inclui algumas aplicações com os IDs.
- **Importar** um ficheiro CSV com a lista de nomes das aplicações e os IDs de pacotes. Ou **Exportar** uma lista existente que inclua as aplicações.

## <a name="kiosk-supervised-only"></a>Quiosque (apenas supervisionado)

- **Aplicação a executar no modo de quiosque**: escolha o tipo de aplicações que quer executar no modo de quiosque. As opções são:
  - **Não configurado**: as definições de quiosque não são aplicadas. O dispositivo não é executado no modo de quiosque.
  - **Aplicação da Loja**: introduza o URL para uma aplicação no iTunes App Store.
  - **Aplicação Gerida**: escolha uma aplicação adicionada ao Intune.
  - **Aplicação Incorporada**: introduza o [ID do pacote](#bundle-ids-for-built-in-ios-apps) (neste artigo) da aplicação incorporada.

- **Toque de apoio**: **Exigir** que a definição de acessibilidade Toque de Apoio esteja ativada no dispositivo. Esta funcionalidade ajuda os utilizadores com os gestos no ecrã que podem ser difíceis para eles. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Inverter cores**: **Exigir** a definição de acessibilidade Inverter Cores para que os utilizadores com deficiências visuais possam ajustar o ecrã de visualização. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Áudio mono**: **Exigir** que a definição de acessibilidade Áudio mono esteja ativada no dispositivo. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **VoiceOver**: **Exigir** que a definição de acessibilidade VoiceOver esteja ativada no dispositivo para a leitura em voz alta do texto no ecrã. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Zoom**: **Exigir** que a definição Zoom esteja ativada no dispositivo para permitir que os utilizadores utilizem o toque para aumentar o zoom no ecrã. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Bloqueio automático**: **Permitir** o bloqueio automático do dispositivo. **Não configurado** desativa esta funcionalidade.
- **Comutador de toque**: **Permitir** o comutador de toque (sem som) no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Rotação do ecrã**: **Permitir** a mudança da orientação do ecrã quando o utilizador rodar o dispositivo. **Não configurado** desativa esta funcionalidade.
- **Botão de suspensão do ecrã**: escolha **Permitir** para desativar o botão de reativação de suspensão do ecrã no dispositivo. **Não configurado** ativa esta funcionalidade.
- **Toque**: **Bloquear** desativa o ecrã tátil do dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **Permitir** a utilização dos botões de volume no dispositivo. **Não configurado** desativa os botões de volume.
- **Controlo de toque de apoio**: **Permitir** permite que os utilizadores utilizem a função de toque de apoio. **Não configurado** desativa esta funcionalidade.
- **Controlo de inversão de cores**: **Permitir** as alterações de inversão de cores para que os utilizadores ajustem a função de inversão de cores. **Não configurado** desativa esta funcionalidade.
- **Falar em texto selecionado**: **Permitir** que as definições de acessibilidade Enunciar Seleção estejam ativadas no dispositivo. Esta funcionalidade lê em voz alta o texto que o utilizador seleciona. **Não configurado** desativa esta funcionalidade.
- **Controlo de VoiceOver**: **Permitir** as alterações ao VoiceOver para que os utilizadores atualizem a função VoiceOver, por exemplo, a rapidez com que o texto no ecrã é lido em voz alta. **Não configurado** impede as alterações ao VoiceOver.
- **Controlo de zoom**: **Permitir** as alterações feitas pelo utilizador ao zoom. **Não configurado** impede as alterações ao zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre a utilização da ferramenta Apple Configurator.
> Se a aplicação iOS que introduziu for instalada após a atribuição do perfil, o dispositivo só entrará em modo de quiosque após ser reiniciado.

## <a name="domains"></a>Domínios

- **Domínios de e-mail não marcados** > **URL do Domínio de E-Mail**: adicione um ou mais URLs à lista. Quando os utilizadores finais receberem um e-mail de um domínio diferentes dos introduzidos, o e-mail será marcado como não fidedigno na aplicação de E-mail do iOS.

- **Domínios Web geridos** > **URL do Domínio Web**: adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzidos, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

- **Domínios de preenchimento automático de palavras-passe do Safari** > **URL do domínio**: adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Esta definição aplica-se apenas ao browser Safari e aos dispositivos iOS 9.3 e posterior no modo supervisionado. Se não especificar nenhum URL, as palavras-passe poderão ser guardadas a partir de todos os sites.

## <a name="bundle-ids-for-built-in-ios-apps"></a>IDs dos pacotes das aplicações iOS incorporadas

A seguinte lista mostra o ID da coleção de pacotes de algumas aplicações iOS comuns incorporadas. Para localizar o ID do pacote de outras aplicações, contacte o fabricante de software.

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
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Definições     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Bolsa       | Apple     |
| com.apple.tips              | Sugestões         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Watch        | Apple     |
| com.apple.weather           | Meteorologia      | Apple     |

## <a name="settings-that-require-supervised-mode"></a>Definições que exigem o modo supervisionado

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
> A Apple confirmou que determinadas definições serão mudadas para o modo apenas supervisionado em 2019. Recomendamos que tenha isto em consideração ao utilizar estas definições em vez de aguardar que a Apple efetue a migração para o modo apenas supervisionado:
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

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [macOS](device-restrictions-macos.md).
