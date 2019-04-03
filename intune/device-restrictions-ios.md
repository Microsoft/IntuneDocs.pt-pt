---
title: definições de dispositivos iOS no Microsoft Intune – Azure | Documentos da Microsoft
titleSuffix: ''
description: Adicionar, configurar ou criar definições em dispositivos iOS para restringir funcionalidades, incluindo a definição de requisitos de palavra-passe, controlar o ecrã bloqueado, utilize aplicações incorporadas, adicionar restrito ou aplicações aprovadas, lidar com dispositivos bluetooth, ligar para a cloud na cópia de segurança e armazenamento, Ativar o modo de local público, adicionar domínios e controlo, como os utilizadores interagem com o browser Safari no Microsoft Intune.
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
ms.sourcegitcommit: 79baf89e4a7a7b1cecb8ccf5cb976736ae6a7286
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58871476"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>definições de dispositivos iOS para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos iOS. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos seus dispositivos iOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de restrições de dispositivos](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Partilhar dados de utilização**: Escolher **bloco** para impedir que o dispositivo de enviar dados de diagnóstico e utilização para a Apple. **Não configurado** (predefinição) permite que estes dados a serem enviados.
  - **Modificação de definições de submissão de diagnósticos (apenas supervisionada)**: **Bloco** impede que o utilizador alterar as definições de análise de submissão e aplicação de diagnóstico no **diagnóstico e utilização** (definições de dispositivo). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

    Esta funcionalidade aplica-se a:  
    - iOS 9.3.2 e posterior

- **Captura de ecrã**: Escolher **bloco** impedir capturas de ecrã ou tela captura no dispositivo. No iOS 9.0 e posterior, este também inclui gravar o ecrã de bloqueio. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.
  - **Observação remota do ecrã pela aplicação Classroom (apenas supervisionada)**: Escolher **bloco** para impedir que a aplicação sala de aula remotamente, ver o ecrã no dispositivo. **Não configurado** (predefinição) permite que a aplicação de sala de aula da Apple ver o ecrã.

    Esta funcionalidade aplica-se a:  
    - iOS 9.3 e posterior

  - **Observação não solicitada do ecrã através da aplicação Classroom (apenas supervisionado)**: Se definido como **permitir**, professores podem observar silenciosamente o ecrã de dispositivos iOS de estudantes através da aplicação Classroom sem o conhecimento dos estudantes. Dispositivos de estudantes inscritos numa classe com a aplicação de sala de aula automaticamente conceder permissão ao professor do curso. **Não configurado** (predefinição) impede que esta funcionalidade.
- **Certificados TLS não fidedignos**: Escolher **bloco** para impedir que os certificados Transport Layer Security (TLS) não fidedignos no dispositivo. **Não configurado** (predefinição) permite que os certificados TLS.
- **Fidedignidade da aplicação empresarial**: Escolher **bloco** para remover o **Trust Enterprise Developer** botão em Definições > geral > perfis e gestão de dispositivos no dispositivo. **Não configurado** (predefinição) permite que o utilizador optar por confiar em aplicações que não são transferidas a partir da loja de aplicações.
- **Modificação da conta (apenas supervisionado)**: Quando definido como **bloco**, o utilizador não é possível atualizar as definições específicas do dispositivo a partir da aplicação de definições do iOS. Por exemplo, o utilizador não é possível criar novas contas de dispositivo, ou alterar o nome de utilizador ou palavra-passe. **Não configurado** (predefinição) permite aos utilizadores alterar estas definições.

  Esta funcionalidade também aplica-se às definições acessíveis a partir da aplicação de definições de iOS, por exemplo, correio, contactos, calendário, Twitter e muito mais. Esta funcionalidade não se aplica a aplicações com as definições da conta que não são configuráveis a partir da aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.
- **Ecrã de tempo (apenas supervisionado)**: Escolher **bloco** para impedir que os utilizadores a definição de suas próprias restrições em tempo de tela (definições do dispositivo). **Não configurado** permite que o usuário configurar restrições de dispositivos (por exemplo, controles dos pais ou conteúdo e as restrições de privacidade) no dispositivo.

  Esta definição foi mudada a partir **ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 e versões anteriores: **Bloco** impede que os utilizadores finais a definição de suas próprias restrições nas definições do dispositivo. Este é o mesmo; e não foram efetuadas alterações para os utilizadores finais.
  - iOS 12.0 e posterior: **Bloco** impede que os utilizadores finais definir seus próprios **ecrã tempo** nas definições do dispositivo (definições > geral > tempo de tela), incluindo restrições de conteúdo e a privacidade. Dispositivos atualizados para o iOS 12.0 não vir o separador de restrições nas definições do dispositivo deixa de poder (definições > geral > Gestão de dispositivos > perfil de gestão > restrições). Estas definições estão em **tempo de tela**.
  
- **Utilização da opção de definições no dispositivo (apenas supervisionado) e apagar todos os conteúdos**: Escolher **bloco** para que os utilizadores não é possível utilizar a opção de definições no dispositivo (apenas supervisionado) e apagar todos os conteúdos. **Não configurado** (predefinição) fornece aos usuários acesso a estas definições.
- **Modificação do nome do dispositivo (apenas supervisionada)**: Escolher **bloco** para que não é possível alterar o nome do dispositivo. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Modificação de definições de notificação (apenas supervisionada)**: Escolher **bloco** para que não não possível alterar as definições de notificação. **Não configurado** (predefinição) permite que o utilizador altere as definições de notificação do dispositivo.
- **Imagem de fundo (apenas supervisionado)**: **Bloco** impede que a imagem de fundo que está a ser alterado. **Não configurado** (predefinição) permite que o utilizador altere a imagem de fundo no dispositivo.
- **(Apenas supervisionado) dos modificação de definições de confiança para aplicações empresariais**: **Bloco** impede o utilizador alterar as definições de fidedignidade de aplicações empresariais em dispositivos supervisionados. **Não configurado** (predefinição) permite ao utilizador confiar em aplicações que não são transferidas a partir da loja de aplicações.
- **Alterações do perfil de configuração (apenas supervisionadas)**: **Bloco** impede alterações do perfil de configuração no dispositivo. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Bloqueio de ativação (apenas supervisionado)**: Escolher **permitir** ativar o bloqueio de ativação de dispositivos iOS supervisionados. Bloqueio de ativação dificulta que um dispositivo perdido ou roubado ser reativado.
- **Bloquear a remoção de aplicações (apenas supervisionada)**: Escolher **bloco** para impedir que os utilizadores a remover aplicações. **Não configurado** (predefinição) permite aos utilizadores remover aplicações do dispositivo.
- **Modo de USB restrito de blocos (apenas supervisionado)**: Escolher **bloco** para desativar o modo restrito de USB em dispositivos supervisionados. Modo restrito de USB bloqueia acessórios USB de troca de dados com um dispositivo que está bloqueado para mais de uma hora. **Não configurado** (predefinição) permite que o modo restrito de USB.
- **Forçar automática data e hora (apenas supervisionado)**: **Exigir** forças supervisionado dispositivos para definir a data e hora automaticamente. Fuso horário do dispositivo é atualizado quando o dispositivo tem ligações via rede móveis ou ativou Wi-Fi com os serviços de localização.
- **Exigir aos alunos para solicitar permissão para deixar o curso em sala de aula (apenas supervisionado)**: **Exigir** força os estudantes inscritos num curso não gerido com a aplicação de sala de aula solicitar permissão do professor deixar o curso. **Não configurado** (predefinição) não força o aluno para pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11.3 e posterior

- **Permitir a sala de aula bloquear a uma aplicação e bloquear o dispositivo sem pedir confirmação (apenas supervisionado)**: **Ativar** permite professor para aplicações de bloquear ou bloquear o dispositivo através da aplicação Classroom sem pedir confirmação de estudante. Meios de aplicações de bloqueio do dispositivo só pode professor de acesso de aplicações especificadas. **Não configurado** (predefinição) impede professores de bloqueio de aplicações ou dispositivos com a aplicação de sala de aula sem pedir confirmação de estudante. 

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Associar automaticamente classes de sala de aula sem pedir confirmação (apenas supervisionado)**: **Ativar** automaticamente permite que os estudantes associar uma classe que está na aplicação de sala de aula sem pedir confirmação o professor. **Não configurado** (predefinição) solicita o professor que os estudantes pretendem associar uma classe que está na aplicação de sala de aula.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Permitir atualizações por ondas eletromagnéticas do PKI**: **Permitir** permite aos usuários receber atualizações de software sem precisar se conectar seus dispositivos a um computador.
- **Ad de limite de controlo**: Escolher **limite** para desativar o identificador de publicidade do dispositivo. **Não configurado** (predefinição) mantém-a ativada.
- **Criação de VPN de bloco (apenas supervisionada)**: **Bloco** impede os utilizadores de criação de definições de configuração de VPN. **Não configurado** (predefinição) permite aos usuários criar VPNs no dispositivo.
- **Modificar as definições de eSIM (apenas supervisionadas)**: **Bloco** impede que os utilizadores de remover ou adicionar um plano de celular para eSIM no dispositivo. **Não configurado** (predefinição) permite aos utilizadores alterar estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12.1 e posterior

- **Diferir atualizações de software (apenas supervisionadas)**: Quando definido como **não configurado** (predefinição), as atualizações de software são apresentadas no dispositivo como Apple as lança. Por exemplo, se uma atualização de iOS obtém lançada pela Apple numa data específica, em seguida, essa atualização naturalmente aparece no dispositivo em torno da data de lançamento.

  **Ativar** permite-lhe atrasar a quando as atualizações de software são apresentadas nos dispositivos, de 0 a 90 dias. Esta definição não controla quando as atualizações são ou não estão instaladas. 

  - **Atrasar a visibilidade das atualizações de software**: Introduza um valor de 0 a 90 dias. Quando expira o atraso, os utilizadores obtêm uma notificação para atualizar para a versão mais antiga do SO disponível quando o atraso foi acionado.

    Por exemplo, se iOS 12.a está disponível no **1º de Janeiro**, e **atrasar visibilidade** está definida como **5 dias**, iOS, em seguida, 12.a não é mostrado como uma atualização disponível nos dispositivos do utilizador final. Sobre o **sexto dia** após o lançamento, que a atualização está disponível, e os utilizadores finais podem instalá-la.

    Esta definição aplica-se a:  
    - iOS 11.3 e posterior

## <a name="password"></a>Palavra-passe

- **palavra-passe**: **Exigir** o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** permite aos utilizadores aceder ao dispositivo sem introduzir uma palavra-passe.
  - **Palavras-passe simples**: Escolher **bloco** solicitar palavras-passe mais complexas. **Não configurado** permite que as palavras-passe simples, como `0000` e `1234`.
  - **Tipo de palavra-passe obrigatório**: Escolha o tipo de palavra-passe necessitam da sua organização. As opções são:
    - **Predefinição do dispositivo**
    - **Numeric**
    - **Alphanumeric**
  - **Número de carateres não alfanuméricos na palavra-passe**: Introduza o número de carateres de símbolo, tal como `#` ou `@`, que têm de ser incluídos na palavra-passe.
  - **Comprimento mínimo da palavra-passe**: Introduza o comprimento mínimo de que um utilizador tem de introduzir (entre 4 e 14 caracteres).
  - **Número de falhas de início de sessão antes de limpar o dispositivo**: Introduza o número de inícios de sessão falhados a permitir antes do dispositivo ser apagado (entre 1 a 11).
  - **Máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida**<sup>1</sup>: Introduza o tempo que o dispositivo permanece inativo antes do utilizador ter de reintroduzir a palavra-passe. Se o tempo que introduzir superior ao atualmente definido no dispositivo, em seguida, o dispositivo ignora o tempo que introduzir. Suportado no iOS 8.0 e dispositivos mais recentes.
  - **Máximo de minutos de inatividade até o ecrã bloquear**<sup>1</sup>: Introduza o número máximo de minutos de inatividade permitido no dispositivo até o ecrã ser bloqueado. Se o tempo que introduzir superior ao atualmente definido no dispositivo, em seguida, o dispositivo ignora o tempo que introduzir.
  - **Expiração de palavra-passe (dias)**: Introduza o número de dias antes da palavra-passe do dispositivo tem de ser alterada.
  - **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de novas palavras-passe que deve ser usado até que pode ser reutilizada uma antiga.
  - **Desbloqueio por impressão digital**: Escolher **bloco** para impedir a utilização de uma impressão digital para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Modificação do código de acesso (apenas supervisionada)**: Escolher **bloco** para parar o código de acesso do que está a ser alterado, adicionado ou removido. Alterações às restrições de código de acesso são ignoradas em dispositivos supervisionados depois de bloqueada a esta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso ser adicionado, alteradas ou removidas.

  - **(Apenas supervisionada) de modificação de impressão digital**: **Bloco** impede o utilizador alterar, adicionar ou remover impressões digitais TouchID. **Não configurado** (predefinição) permite a atualização do utilizador de impressões digitais TouchID no dispositivo.

- **Palavra-passe de bloco preenchimento automático (apenas supervisionado)**: Escolher **bloco** para impedir a utilização da funcionalidade de palavras-passe de preenchimento automático no iOS. Escolher **bloco** também faz o seguinte:

  - Os utilizadores não são-lhe pedidos para utilizar uma palavra-passe guardada no Safari ou em todas as aplicações.
  - Palavras-passe forte de automáticas estão desativadas e as palavras-passe fortes não são sugeridas para os utilizadores.

  **Não configurado** (predefinição) permite que esses recursos.

- **Bloquear pedidos de proximidade de palavra-passe (apenas supervisionados)**: Escolher **bloco** para que o dispositivo de um utilizador não solicitar palavras-passe do dispositivos próximos. **Não configurado** (predefinição) permite que estes pedidos de palavra-passe.
- **Bloquear a partilha de palavra-passe (apenas supervisionado)**: **Bloco** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe a ser partilhado.
- **Exigir a autenticação do Touch ID ou o Face ID para obter informações de palavra-passe ou cartão de crédito preenchimento automático (apenas supervisionado)**: Quando definido como **requerem**, os utilizadores tem de ser autenticado utilizando o touch ID ou o face ID antes de palavras-passe ou as informações de cartão de crédito podem ser automaticamente preenchido Safari e outras aplicações. **Não configurado** (predefinição) permite aos usuários controlar esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

<sup>1</sup>ao configurar o **máximo de minutos de inatividade até o ecrã bloquear** e **máximo de minutos após o bloqueio de ecrã antes de palavra-passe é exigida** definições, estas são aplicadas em sequência. Por exemplo, se definir o valor das duas definições para **5** minutos, a ecrã desliga automaticamente passados cinco minutos e o dispositivo é bloqueado após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, depois do utilizador desliga o ecrã, o dispositivo ser bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

- **Acesso de centro de controlo enquanto o dispositivo está bloqueado**: Escolher **bloco** para impedir o acesso à aplicação Centro de controlo quando o dispositivo está bloqueado. **Não configurado** permite aos utilizadores acesso à aplicação Centro de controlo quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: **Bloco** impede o acesso a notificações quando o dispositivo está bloqueado. **Não configurado** permite ao utilizador aceder as notificações sem desbloquear o dispositivo.
- **Notificações de carteira, enquanto o dispositivo está bloqueado**: **Bloco** impede o acesso à aplicação Carteira quando o dispositivo está bloqueado. **Não configurado** permite ao utilizador aceder à aplicação de carteira, enquanto o dispositivo está bloqueado.
- **Vista hoje enquanto o dispositivo está bloqueado**: **Bloco** impede o acesso para a vista hoje enquanto o dispositivo está bloqueado. **Não configurado** permite ao utilizador ver a vista hoje enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

- **Loja de aplicações**: **Bloco** impede o acesso à loja de aplicações em dispositivos supervisionados. **Não configurado** permite o acesso.
  - **Instalar aplicações da Store da aplicação (apenas supervisionado)**: Escolher **bloco** para bloquear a app store a partir do ecrã principal do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** permite que a loja de aplicações no ecrã inicial.
  - **Transferências automáticas de aplicações (apenas supervisionadas)**: Escolher **bloco** para impedir a transferência automática de aplicações compradas noutros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** permite que as aplicações compradas noutros dispositivos iOS para transferir no dispositivo.
- **Palavra-passe para aceder à loja de aplicações**: **Exigir** ao utilizador para introduzir uma palavra-passe antes de poderem visitar a loja de aplicações. **Não configurado** permite o acesso à loja de aplicações, sem introduzir uma palavra-passe.
- **Compras na aplicação**: Escolher **bloco** para impedir que as compras na aplicação da loja. **Não configurado** permite compras na loja uma aplicação em execução.
- **Conteúdo de música, podcast ou notícias do explícito do iTunes (apenas supervisionado)**: Escolher **bloco** para impedir que o conteúdo de música, podcast ou notícias explícito do iTunes. **Não configurado** permite que o dispositivo aceda ao conteúdo classificado como conteúdo para adultos na loja.
- **Transferir conteúdos da iBook store identificados como "Erótico"**: Escolher **bloco** para impedir que os utilizadores de deixar de transferir o suporte de dados a partir da iBook store que é identificada como erótica. **Não configurado** permite ao utilizador transferir livros da categoria "Erótico".
- **Ver documentos empresariais em aplicações não geridas**: **Bloco** impede a ver documentos empresariais em aplicações não geridas. **Não configurado** permite que os documentos empresariais sejam vistos em qualquer aplicação. Por exemplo, pretende impedir que os utilizadores guardar ficheiros a partir da aplicação OneDrive no Dropbox. Configurar esta definição como **bloco**. Depois do dispositivo receber a política (por exemplo, após um reinício), já não permite a guardar.
  - **Permitir que aplicações geridas escrever contactos para contas de não-gerenciado contactos**: Quando definido como **permitir**, os utilizadores podem adicionar ou sincronizar Outlook informações de contacto qualquer pessoa, incluindo empresas e contactos de empresa, para a aplicação incorporada de contactos no dispositivo. Quando definido como **não configurado**, os utilizadores não é possível adicionar a contatos do Outlook para a aplicação incorporada de contactos no dispositivo.
  
    Para utilizar esta definição, defina o **ver documentos empresariais em aplicações não geridas** definição **bloco**.
  
- **Ver documentos não empresariais em aplicações empresariais**: **Bloco** impede a ver documentos não empresariais em aplicações empresariais. **Não configurado** permite que qualquer documento seja visto em aplicações geridas empresariais.
  - **Permitir aplicações não geridas ler contactos geridos de contas de**: Quando definido como **permitir**, os usuários podem adicionar iContacts aplicação informações de contato qualquer pessoa no Outlook. **Não configurado** impede que duplicatas de remoção de ler, incluindo, a partir da aplicação incorporada de contactos no dispositivo.
  
    Para utilizar esta definição, defina o **ver documentos não empresariais em aplicações empresariais** definição **bloco**.
  
- **Tratar o AirDrop como um destino não gerido**: **Exigir** força o AirDrop a ser considerado um destino não gerido. Ele impede que as aplicações geridas de enviar dados através de Airdrop. 
- **Adicionar amigos do Game Center (apenas supervisionados)**: **Bloco** impede os utilizadores de adição de amigos do Game Center. **Não configurado** permite que o utilizador adicione amigos no Centro de jogos.
- **Centro de jogos (apenas supervisionado)**: **Bloco** a utilização da aplicação Game Center. **Não configurado** permite utilizar a aplicação do Centro de jogos no dispositivo.
- **Jogos de multijogadores (apenas supervisionado)**: Escolher **bloco** para impedir que os jogos de vários jogadores. **Não configurado** permite que o utilizador Jogue jogos multijogador no dispositivo.
- **Região das classificações**: Escolha a região das classificações que pretende utilizar para transferências permitidas. E, em seguida, selecione as classificações permitidas para **filmes** e **TV mostra**.
- **Aplicações**: Selecione a classificação etária permitida das aplicações que os utilizadores podem transferir ou pode escolher **permitir todas as aplicações**.

## <a name="built-in-apps"></a>Aplicações Incorporadas

- **Câmara**: Escolher **bloco** para impedir o acesso à câmara do dispositivo. **Não configurado** permite o acesso à câmara do dispositivo.
  - **FaceTime**: **Bloco** para impedir o acesso à aplicação FaceTime. **Não configurado** permite o acesso à aplicação FaceTime no dispositivo.
- **Siri**: **Bloco** impede o acesso a Siri. **Não configurado** permite usando o Assistente de voz Siri no dispositivo.
  - **Siri enquanto o dispositivo está bloqueado**: Escolher **bloco** para impedir o acesso a Siri quando o dispositivo está bloqueado. **Não configurado** permite usando o Assistente de voz Siri no dispositivo quando ele está bloqueado.
  - **Filtro de linguagem inapropriada da Siri (apenas supervisionado)**: **Exigir** impede que a Siri Dite ou fale com linguagem profana.
  - **A siri pode consultar conteúdos gerados pelo utilizador da internet (apenas supervisionado)**: **Bloco** impede a Siri de aceder ao Web sites para responder a perguntas. **Não configurado** permite que a siri pode aceder a conteúdos gerados pelo utilizador a partir da internet.
- **Apple News (apenas supervisionado)**: Escolher **bloco** para impedir o acesso à aplicação Apple News no dispositivo. **Não configurado** permite utilizar a aplicação Apple News.
- **loja iBooks (apenas supervisionada)**: **Bloco** impede o acesso à iBooks store. **Não configurado** permite aos utilizadores procurar e compre livros da loja iBooks.
- **Aplicação mensagens no dispositivo (apenas supervisionado)**: Escolher **bloco** para que os utilizadores não é possível utilizar a aplicação de mensagens no dispositivo. **Não configurado** permite utilizar a aplicação de mensagens para enviar e ler mensagens de texto.
- **Podcasts (apenas supervisionado)**: **Bloco** impede que os utilizadores através da aplicação Podcasts. **Não configurado** permite a utilização da aplicação Podcasts.
- **Serviço Music (apenas supervisionado)**: **Bloco** reverte o aplicativo de música para o modo clássico e desativa o serviço de música. **Não configurado** permite o uso de aplicação Apple Music.
- **serviço iTunes Radio (apenas supervisionado)**: **Bloco** impede os utilizadores de utilizar a aplicação iTunes Radio. **Não configurado** permite o uso de aplicação iTunes Radio.
- **Alterações às definições da aplicação encontrar amigos (apenas supervisionadas)**: **Bloco** impede alterações às definições da aplicação Find My Friends. **Não configurado** permite que o utilizador altere as definições da aplicação Find My Friends.
- **Pesquisa Spotlight para devolver resultados da internet (apenas supervisionado)**: **Bloco** impede o destaque do retorno de resultados de uma pesquisa na Internet. **Não configurado** permite destaque pesquisa ligar à Internet para fornecer os resultados da pesquisa.
- **Bloquear a remoção de aplicações do sistema do dispositivo (apenas supervisionado)**: Escolher **bloco** desativa a capacidade de remover aplicações de sistema do dispositivo. **Não configurado** permite aos utilizadores remover aplicações do sistema.

#### <a name="safari"></a>Safari

- **Safari (apenas supervisionado)**: **Bloco** utilização do browser Safari no dispositivo. **Não configurado** permite que os utilizadores a utilizar o browser Safari.
- **Preenchimento automático**: **Bloco** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** permite que os utilizadores alterem as definições do browser.
- **Cookies**: Escolha a forma como os cookies são processados no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual
- **JavaScript**: **Bloco** impede que os scripts em Java no browser em execução no dispositivo. **Não configurado** permite que os scripts de Java.
- **Avisos de fraude**: **Exigir** avisos de fraude para ser mostrada no navegador da web no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Pop-ups**: **Bloco** para desativar o Bloqueador de pop-up no browser. **Não configurado** permite que o Bloqueador de pop-up.

## <a name="restricted-apps"></a>Aplicações restritas

Na lista de aplicações restritas, pode configurar uma das seguintes listas:

- **Aplicações proibidas**: Uma lista de aplicações não geridas pelo Intune que não quer instalada no dispositivo. Se um usuário instala uma aplicação a partir desta lista, é notificado pelo Intune.
- **Aplicações aprovadas**: Uma lista de aplicações que os utilizadores podem instalar. Para ficar em conformidade, os utilizadores não podem instalar outras aplicações. As aplicações geridas pelo Intune são automaticamente permitidas. Se um usuário instala uma aplicação a partir desta lista, é notificado pelo Intune.

Adicionar aplicações para estas listas, pode:

- **Adicionar** a aplicação na iTunes store URL da aplicação que pretende. Por exemplo, para adicionar a aplicação pastas de trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Pode também utilizar o iTunes para localizar a aplicação e, em seguida, utilizar o **copiar ligação** tarefa para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Em alternativa, exportar uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Perfis de dispositivos que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar ou ocultar aplicações (apenas supervisionado)

Na lista de aplicações Mostrar ou ocultar, pode configurar uma das seguintes listas em dispositivos supervisionados com o iOS 9.3 ou mais recente.

- **Aplicações ocultas**: Introduza uma lista de aplicações que estão ocultos dos utilizadores. Os utilizadores não podem ver ou abra estas aplicações.
- **Aplicações visíveis**: Introduza uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

Adicionar aplicações para estas listas, pode:

- **Adicionar** a aplicação na iTunes store URL da aplicação que pretende. Por exemplo, para adicionar a aplicação pastas de trabalho da Microsoft, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Pode também utilizar o iTunes para localizar a aplicação e, em seguida, utilizar o **copiar ligação** tarefa para obter o URL da aplicação.

- Importe um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Em alternativa, exportar uma lista existente, que inclui a lista de aplicações restritas no mesmo formato.

## <a name="wireless"></a>Sem fios

- **Roaming de dados**: Escolher **bloco** para impedir que os dados em roaming na rede celular. **Não configurado** (predefinição) permite que os dados em roaming quando o dispositivo estiver numa rede celular.
- **Obtenção de segundo plano global roaming**: **Bloco** impede a utilizar a funcionalidade de obtenção de em segundo plano global quando em roaming na rede celular. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, tais como e-mail, quando está em roaming numa rede celular.
- **Marcação por voz**: Escolher **bloco** para impedir que os utilizadores a utilizar a funcionalidade de marcação por voz no dispositivo. **Não configurado** (predefinição) permite as chamadas discar no dispositivo.
- **Chamadas em roaming**: Escolher **bloco** para impedir que chamadas em roaming na rede celular. **Não configurado** (predefinição) permite chamadas em roaming quando o dispositivo estiver numa rede celular.
- **Alterações às definições de utilização de dados via rede móvel de aplicação (apenas supervisionadas)**: Escolher **bloco** para impedir alterações às definições de utilização de dados via rede móvel da aplicação. **Não configurado** (predefinição) permite que o utilizador controle que aplicações estão autorizadas a utilizar dados via rede móvel.
- **Alterações às definições de plano via rede móvel (apenas supervisionadas)**: **Bloco** impede os utilizadores de alterar quaisquer definições no plano de celular. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

- **Hotspot pessoal**: **Bloco** se desligar a hotspot pessoal no dispositivo dos utilizadores com cada sincronização do dispositivo. Esta definição poderá não ser compatível com algumas operadoras. **Não configurado** (predefinição) mantém a configuração de hotspot pessoal, como o padrão definido pelo utilizador.
- **Junte-se a redes Wi-Fi apenas com perfis de configuração (apenas supervisionados)**: **Exigir** força o dispositivo para utilizar apenas as redes Wi-Fi configuradas através de perfis de configuração do Intune. **Não configurado** (predefinição) permite que o dispositivo utilizar a outras redes Wi-Fi.
- **Regras de utilização de rede móvel (apenas aplicações geridas)**: Defina os dados de tipos de aplicações geridas podem utilizar em redes de celular. As opções são:
  - **Bloquear a utilização de dados via rede móvel**: Bloquear a utilizar dados via rede móvel para **todas as aplicações geridas** ou **escolher aplicações específicas**.
  - **Bloquear a utilização de dados via rede móvel ao efetuar o roaming**: Bloquear a utilizar dados via rede móvel ao efetuar o roaming para **todas as aplicações geridas** ou **escolher aplicações específicas**.

## <a name="connected-devices"></a>Dispositivos Ligados

- **AirDrop (apenas supervisionado)**: **Bloco** impede o AirDrop a utilizar no dispositivo. **Não configurado** (predefinição) permite o uso da funcionalidade AirDrop para trocar conteúdos com dispositivos próximos.
- **Emparelhamento do Apple Watch (apenas supervisionado)**: **Bloco** impede o emparelhamento com um Apple Watch. **Não configurado** (predefinição) permite que o dispositivo se emparelhe com um Apple Watch.
- **Deteção de pulso para do Apple Watch emparelhado**: **Exigir** força um Apple Watch emparelhado a utilizar a deteção de pulso. Quando for necessário, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 
- **Modificação de Bluetooth (apenas supervisionada)**: **Bloco** impede o utilizador final a alterar as definições de Bluetooth no dispositivo. **Não configurado** (predefinição) permite ao utilizador alterar estas definições.
- **Emparelhamento de anfitriões para controlar os dispositivos com um dispositivo iOS pode emparelhar (apenas supervisionado)**: **Não configurado** (predefinição) permite o emparelhamento de anfitriões para permitir que o controle de administrador que dispositivos um dispositivo iOS pode emparelhar. **Bloco** impede que o emparelhamento de anfitriões.
- **Exigir palavra-passe de emparelhamento para pedidos de saída do AirPlay**: **Exigir** uma palavra-passe emparelhada quando o utilizador utiliza AirPlay transmitir conteúdos para outros dispositivos da Apple. **Não configurado** (predefinição) permite que o usuário transmitir conteúdo com o AirPlay sem introduzir uma palavra-passe.
- **AirPrint de bloco (apenas supervisionado)**: Escolher **bloco** para impedir a utilizar a funcionalidade de AirPrint no dispositivo. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Bloquear o armazenamento de credenciais do AirPrint na Keychain (apenas supervisionado)**: **Bloco** impede a utilizar o armazenamento de Keychain para o nome de utilizador e palavra-passe no dispositivo. **Não configurado** (predefinição) permite armazenar o nome de utilizador do AirPrint e a palavra-passe na aplicação Keychain.
  - **Exigir um certificado fidedigno do TLS para AirPrint (apenas supervisionado)**: **Exigir** força o dispositivo para utilizar certificados fidedignos para comunicação de impressão de TLS.
  - **Deteção de iBeacon do bloco de impressoras com o AirPrint (apenas supervisionado)**: **Bloco** impede maliciosos AirPrint Bluetooth beacons de phishing para tráfego de rede. **Não configurado** (predefinição) permite que o anúncio de impressoras com o AirPrint no dispositivo.
- **Bloquear a definição de cópia de segurança de novo nas proximidades de dispositivos (apenas supervisionados)**: **Bloco** desativa a linha de comandos para configurar novos dispositivos que estejam próximos. **Não configurado** (predefinição) permite que os pedidos para os utilizadores liguem a dispositivos próximos em Apple.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e posterior

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

- **Pesquisa de definição de palavras (apenas supervisionada)**: **Bloco** impede o utilizador de realçar uma palavra e, em seguida, procurar a respetiva definição no dispositivo. **Não configurado** permite o acesso para o recurso de pesquisa de definição.
- **Teclados preditivos (apenas supervisionados)**: **Não configurado** permite a utilização de teclados preditivos para sugerem palavras que o utilizador pode desejar. **Bloco** impede que esta funcionalidade.
- **Correção automática (apenas supervisionada)**: **Não configurado** permite que o dispositivo corrija automaticamente palavras com erros ortográficos. **Bloco** impede autocorrection a utilizar.
- **(Apenas supervisionada) de verificação ortográfica do teclado**: **Não configurado** permite o uso de verificador ortográfico do dispositivo. **Bloco** permite que o verificador ortográfico.
- **(Apenas supervisionados) de atalhos de teclado**: **Não configurado** permite o uso de atalhos de teclado no dispositivo. **Bloco** impede o utilizador utilizar atalhos de teclado.
- **Ditado (apenas supervisionado)**: **Bloco** impede o utilizador através de entradas de voz para introduzir texto. **Não configurado** permite que o utilizador utilize a entrada de ditado.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Cópia de segurança para iCloud**: **Não configurado** permite ao utilizador efetuar cópias de segurança do dispositivo para iCloud. **Bloco** impede o utilizador de cópias de segurança de dispositivo para iCloud.
- **Bloquear a sincronização de documentos (apenas supervisionado) do iCloud**: **Não configurado** permite a sincronização de documentos e chave-valor para o seu espaço de armazenamento do iCloud. **Bloco** impede a sincronização de documentos e dados de iCloud.
- **Fotografia stream sincronizados com o iCloud**: **Não configurado** permite aos utilizadores ativar **minha fotografia Stream** no respetivo dispositivo sincronizadas com o iCloud e ter fotos disponíveis nos dispositivos do utilizador. **Bloco** impede a fotografia stream sincronizados com o iCloud.
- **Cópia de segurança encriptada**: **Exigir** para cópias de segurança do dispositivo tem de estar encriptadas.
- **Fototeca em iCloud**: Defina como **bloco** para desativar a utilizar a biblioteca de fotografias do iCloud para armazenar fotografias e vídeos na cloud. Qualquer fotos não sido completamente transferidas da Fototeca em iCloud para o dispositivo são removidas do dispositivo. **Não configurado** permite o uso da biblioteca de fotografias do iCloud.
- **Sincronização das aplicações na cloud geridas**: **Não configurado** permite que as suas aplicações gere o Intune sincronizem dados para a conta de utilizador iCloud. **Bloco** impede que a sincronização de dados para o iCloud.
- **Transmissão partilhada de fotografias**: Escolher **bloco** para desativar **partilha de fotografias do iCloud** no dispositivo. **Não configurado** permite a transmissão em fluxo de fotografias partilhadas.
- **Continuação da atividade**: **Não configurado** permite aos utilizadores continuar o trabalho que iniciou num dispositivo iOS noutro dispositivo de iOS ou macOS (Handoff). **Bloco** impede este handoff.
- **Bloquear a sincronização de Keychain do iCloud**: Escolher **bloco** para desativar a sincronização credenciais armazenadas na Keychain com o iCloud. **Não configurado** permite que os usuários sincronizar estas credenciais.
- **Bloquear a cópia de segurança de livro de Enterprise**: Escolher **bloco** impedir os utilizadores de backup de livros de enterprise. **Não configurado** permite aos utilizadores criar cópias de segurança estes manuais.
- **Bloquear a sincronização de metadados de livro enterprise (notas e destaques)**: **Bloco** impede que sincronize notas e destaques em livros do enterprise. **Não configurado** permite que a sincronização.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicação única autónomo (apenas supervisionado)

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo está bloqueado. Só pode ser executado essa aplicação. Por exemplo, adicione uma aplicação que permite aos utilizadores fazer um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

Adicionar aplicações, pode:

- Introduza o **nome da aplicação** e **ID do pacote de aplicação**e selecione **Add**. [IDs de pacote para aplicações iOS incorporadas](#bundle-ids-for-built-in-ios-apps) (Este artigo) inclui algumas aplicações com suas IDs.
- **Importar** um ficheiro CSV com a lista de nomes de aplicações e os IDs de coleção. Ou, **exportar** uma lista existente, que inclui as aplicações.

## <a name="kiosk-supervised-only"></a>Quiosque (apenas supervisionado)

- **Aplicação seja executada no modo de quiosque**: Escolha o tipo de aplicações que pretende executar no modo de local público. As opções são:
  - **Não configurado**: Não são aplicadas definições de local público. O dispositivo não é executado no modo de local público.
  - **Aplicação de Store**: Introduza o URL para uma aplicação na App store do iTunes.
  - **Aplicação gerida**: Selecione uma aplicação que adicionar ao Intune.
  - **Aplicação incorporada**: Introduza o [ID de pacote](#bundle-ids-for-built-in-ios-apps) (neste artigo) da aplicação incorporada.

- **Toque de apoio**: **Exigir** a definição de acessibilidade Assistivetouch estar no dispositivo. Esta funcionalidade ajuda os utilizadores na tela gestos, que podem ser difícil para eles. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Inverter cores**: **Exigir** a definição de acessibilidade de inverter cores para os utilizadores com deficiências visuais possam alterar a tela de apresentação. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Áudio mono**: **Exigir** a definição de acessibilidade áudio Mono estar no dispositivo. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **VoiceOver**: **Exigir** a definição de acessibilidade de VoiceOver ser no dispositivo para a leitura em voz alta o texto na tela. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Zoom**: **Exigir** a definição de Zoom de ser no dispositivo para permitir que os utilizadores a utilizar o toque para aumentar o zoom no ecrã. **Não configurado** não executar ou habilitar esse recurso no modo de local público.
- **Bloqueio automático**: **Permitir** bloqueio automático do dispositivo. **Não configurado** desativa esta funcionalidade.
- **Comutador do toque**: **Permitir** mudar da alteração do toque (desativar som) no dispositivo. **Não configurado** desativa esta funcionalidade.
- **Rotação do ecrã**: **Permitir** mudança da orientação do ecrã quando o utilizador roda o dispositivo. **Não configurado** desativa esta funcionalidade.
- **Botão de suspensão do ecrã**: Escolher **permitir** para desativar o botão de reativação de suspensão do ecrã no dispositivo. **Não configurado** habilita esse recurso.
- **Touch**: **Bloco** desativa o ecrã tátil do dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **Permitir** utilizando os botões de volume no dispositivo. **Não configurado** desativa os botões de volume.
- **Controlo tátil de apoio**: **Permitir** permitem que os utilizadores utilizem a função assistivetouch. **Não configurado** desativa esta funcionalidade.
- **Controlo de cores de inversão de**: **Permitir** inverter as alterações de cor para permitir aos utilizadores ajustar a função Inverter cores. **Não configurado** desativa esta funcionalidade.
- **Falar em texto selecionado**: **Permitir** as definições de acessibilidade enunciar seleção estar no dispositivo. Esta funcionalidade lê o texto que o utilizador seleciona em voz alta. **Não configurado** desativa esta funcionalidade.
- **Controlo de voiceOver**: **Permitir** alterações voiceover para permitir aos utilizadores atualizar a função VoiceOver, por exemplo, a rapidez na tela de leitura do texto em voz alta. **Não configurado** impede alterações voiceover.
- **Controlo de zoom**: **Permitir** zoom alterações pelo utilizador. **Não configurado** impede alterações de zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre como utilizar a ferramenta Apple Configurator.
> Se a aplicação iOS a que introduzir estiver instalada depois de atribuir o perfil, em seguida, o dispositivo não introduza o modo de local público até que o dispositivo é reiniciado.

## <a name="domains"></a>Domínios

- **Domínios de e-mail não marcados** > **URL de domínio de E-Mail**: Adicione um ou mais URLs à lista. Quando os utilizadores finais recebem um e-mail de um domínio não os domínios que introduzir, o e-mail é marcado como não fidedigno na aplicação Mail do iOS.

- **Domínios web geridos** > **URL de domínio do Web**; Adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzir, que sejam considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

- **Domínios de preenchimento automático de palavras-passe do Safari** > **URL de domínio**: Adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Esta definição aplica-se apenas ao browser Safari e aos dispositivos iOS 9.3 e posterior no modo supervisionado. Se não especificar nenhum URL, as palavras-passe poderão ser guardadas a partir de todos os sites.

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

## <a name="settings-that-require-supervised-mode"></a>As definições que exigem o modo supervisionado

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
> A Apple confirmou que determinadas definições serão movidas para apenas supervisionado em 2019. Recomendamos que tenha isto em consideração ao utilizar estas definições, em vez de aguardar a Apple para migrá-los para apenas supervisionado:
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

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode restringir funcionalidades do dispositivo e definições no [macOS](device-restrictions-macos.md) dispositivos.
