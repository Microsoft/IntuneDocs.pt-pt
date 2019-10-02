---
title: Definições dos dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione, configure ou crie configurações em dispositivos iOS para restringir recursos, incluindo a definição de requisitos de senha, controle a tela bloqueada, use aplicativos internos, adicione aplicativos restritos ou aprovados, manipule dispositivos Bluetooth, conecte-se à nuvem para backup e armazenamento, Habilite o modo de quiosque, adicione domínios e controle como os usuários interagem com o navegador da Web do Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bcd86cedc7684f31483d7cd3c8294a76a9c306b2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730768"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>configurações do dispositivo iOS e iPadOS para permitir ou restringir recursos usando o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações que você pode controlar em dispositivos iOS e iPadOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos iOS.

> [!TIP]
> Essas configurações usam as configurações de MDM da Apple. Para obter mais informações sobre essas configurações, consulte [configurações de gerenciamento de dispositivo móvel da Apple](https://support.apple.com/guide/mdm/welcome/web) (abre o site da Apple).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Essas configurações se aplicam a diferentes tipos de registro, com algumas configurações sendo aplicadas a todas as opções de registro. Para obter mais informações sobre os diferentes tipos de registro, consulte [registro do IOS](../ios-enroll.md).

## <a name="general"></a>Geral

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Partilhar dados de utilização**: escolha **Bloquear** para impedir que o dispositivo envie dados de diagnóstico e de utilização à Apple. **Não configurado** (predefinição) permite que estes dados sejam enviados.

- **Captura de ecrã**: escolha **Bloquear** para impedir as capturas de ecrã no dispositivo. No iOS 9,0 e mais recente, ele também bloqueia gravações de tela. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Certificados TLS não fidedignos**: escolha **Bloquear** para impedir os certificados Transport Layer Security (TLS) não fidedignos no dispositivo. **Não configurado** (predefinição) permite os certificados TLS.
- **Permitir atualizações PKI por ondas eletromagnéticas**: **Permitir** deixa que os utilizadores recebam atualizações de software sem precisarem de ligar os dispositivos a um computador.
- **Limitar rastreio de anúncios**: escolha **Limitar** para desativar o identificador de publicidade do dispositivo. **Não configurado** (predefinição) mantém-no ativado.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Modificação das configurações de envio de diagnóstico**: **Bloquear** impede que o utilizador altere as definições da análise da aplicação e da submissão de diagnóstico em **Diagnóstico e Utilização** (Definições do dispositivo). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

  Para usar essa configuração, defina a configuração **compartilhar dados de uso** como **Bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3.2 e mais recente

- **Observação de tela remota por aplicativo de sala de aula**: escolha **Bloquear** para impedir que a aplicação Classroom veja remotamente o ecrã no dispositivo. **Não configurado** (predefinição) permite que a aplicação Classroom da Apple veja o ecrã.

  Para usar essa configuração, defina a configuração de **captura de tela** como **Bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9,3 e mais recente

- **Observação de tela não solicitada por aplicativo de sala de aula**: se definido como **Permitir**, os professores podem observar o ecrã dos dispositivos iOS dos estudantes de forma silenciosa através da aplicação Classroom sem o conhecimento dos estudantes. Os dispositivos de estudantes inscritos numa turma através da aplicação Classroom concedem automaticamente permissão ao professor do curso. **Não configurado** (predefinição) impede esta funcionalidade.

  Para usar essa configuração, defina a configuração de **captura de tela** como **Bloquear**.

- **Confiança das aplicações empresariais**: escolha **Bloquear** para remover o botão **Confiar no Programador Empresarial** em Definições > Geral > Perfis e Gestão de Dispositivos no dispositivo. **Não configurado** (predefinição) permite que o utilizador opte por confiar nas aplicações que não são transferidas da App Store.
- **Modificação da conta**: quando definido como **Bloquear**, o utilizador não pode atualizar as definições específicas do dispositivo na aplicação de definições do iOS. Por exemplo, o utilizador não pode criar contas novas no dispositivo nem alterar o nome de utilizador ou a palavra-passe. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade também se aplica às definições acessíveis na aplicação de definições do iOS, tais como o Correio, Contactos, Calendário, Twitter e outros. A funcionalidade não se aplica a aplicações com definições da conta que não sejam configuráveis na aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.

- **Hora da tela**: escolha **Bloquear** para impedir que os utilizadores definam as suas próprias restrições em Tempo do Ecrã (definições do dispositivo). **Não configurado** permite que o utilizador configure as restrições do dispositivo (por exemplo, as restrições de acesso ou as restrições de conteúdo e de privacidade) no dispositivo.

  O nome desta definição foi mudado em **Ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 e anterior: **Bloquear** impede que os utilizadores finais definam as suas próprias restrições nas definições do dispositivo. O comportamento é o mesmo; e não há nenhuma alteração para os usuários finais.
  - iOS 12,0 e mais recente: **Bloquear** impede que os utilizadores finais definam o seu próprio **Tempo do Ecrã** nas definições do dispositivo (Definições > Geral > Tempo do Ecrã), incluindo as restrições de conteúdo e de privacidade. Os dispositivos atualizados para o iOS 12.0 deixam apresentar o separador de restrições nas definições do dispositivo (Definições > Geral > Gestão de Dispositivos > Perfil de Gestão > Restrições). Estas definições estão em **Tempo do Ecrã**.
  
- **Uso da opção apagar todo o conteúdo e as configurações no dispositivo**: Escolha **Bloquear** para que os usuários não possam usar a opção apagar todo o conteúdo e as configurações no dispositivo. **Não configurado** (predefinição) concede aos utilizadores acesso a estas definições.
- **Modificação do nome do dispositivo**: escolha **Bloquear** para que não seja possível alterar o nome do dispositivo. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Modificação das configurações de notificação**: escolha **Bloquear** para que não seja possível alterar as definições de notificação. **Não configurado** (predefinição) permite ao utilizador alterar as definições de notificação do dispositivo.
- **Modificação de papel de parede**: **Bloquear** impede que a imagem de fundo seja alterada. **Não configurado** (predefinição) permite ao utilizador alterar a imagem de fundo no dispositivo.
- **Modificação das configurações de confiança do aplicativo empresarial**: **Bloquear** impede que o utilizador altere as definições de confiança das aplicações empresariais nos dispositivos supervisionados. **Não configurado** (predefinição) permite que o utilizador confie nas aplicações que não são transferidas da App Store.
- **Alterações do perfil de configuração**: **Bloquear** impede que o perfil de configuração seja alterado no dispositivo. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Bloqueio de ativação**: escolha **Permitir** para ativar o Bloqueio de Ativação nos dispositivos iOS supervisionados. O Bloqueio de Ativação dificulta que um dispositivo perdido ou roubado seja reativado.
- **Bloquear remoção de aplicativo**: escolha **Bloquear** para impedir que os utilizadores removam aplicações. **Não configurado** (predefinição) permite que os utilizadores removam aplicações do dispositivo.
- **Bloqueia o modo restrito USB**: escolha **Bloquear** para desativar o modo USB Restrito nos dispositivos supervisionados. O modo USB Restricted impede que os acessórios USB mudem de dados com um dispositivo bloqueado por mais de uma hora. **Não configurado** (predefinição) permite o modo USB Restrito.
- **Forçar data e hora automáticas**: **Exigir** força os dispositivos supervisionados a definir automaticamente a Data e a Hora. O fuso horário do dispositivo é atualizado quando o dispositivo está ligado à rede móvel ou ao Wi-Fi com os serviços de localização ativados.
- **Exigir que os alunos solicitem permissão para sair do curso da sala de aula**: **Exigir** força os estudantes inscritos num curso não gerido através do Classroom a pedir permissão ao professor para saírem do curso. **Não configurado** (predefinição) não força o estudante a pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11,3 e mais recente

- **Permitir que a sala de aula bloqueie um aplicativo e bloqueie o dispositivo sem avisar**: **Ativar** permite que o professor bloqueie aplicações ou bloqueie o dispositivo através da aplicação Classroom sem avisar o estudante. Bloquear aplicações significa que o dispositivo pode apenas aceder às aplicações especificadas pelo professor. **Não configurado** (predefinição) impede que os professores bloqueiem aplicações ou dispositivos através da aplicação Classroom sem avisar o estudante.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Unir automaticamente as classes da sala de aula sem avisar**: **Ativar** permite automaticamente que os estudantes adiram a uma turma da aplicação Classroom sem pedir ao professor. **Não configurado** (predefinição) aviso o professor que os estudantes querem aderir a uma turma da aplicação Classroom.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Bloquear a criação de VPN**: **Bloquear** impede que os utilizadores criem definições de configuração de VPN. **Não configurado** (predefinição) deixa que os utilizadores criem VPNs no dispositivo.
- **Modificando configurações do Esim**: **Bloquear** impede que os utilizadores removam ou adicionem um plano da rede móvel ao eSIM no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12,1 e mais recente

- **Adiar atualizações de software**: quando definido como **Não configurado** (predefinição), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização do iOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar visibilidade das atualizações de software**: introduza um valor entre 0 e 90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se iOS 12.a estiver disponível a **1 de janeiro** e a opção **Adiar visibilidade** estiver definida como **5 dias**, a iOS 12.a não será mostrado como uma atualização disponível nos dispositivos do utilizador final. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta definição aplica-se a:  
    - iOS 11,3 e mais recente

## <a name="password"></a>Palavra-passe

> [!NOTE]
> Em uma versão futura, essas configurações de senha na interface do usuário do Intune estão sendo atualizadas para corresponder ao tipo de registro.

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** (padrão) permite que os usuários acessem o dispositivo sem inserir uma senha.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

> [!IMPORTANT]
> Em dispositivos registrados pelo usuário, se você definir qualquer configuração de senha, as configurações de **senhas simples** serão automaticamente definidas como **Bloquear**e um PIN de 6 dígitos será imposto.
>
> Por exemplo, você define a configuração de **expiração de senha** e envia por push essa política para dispositivos registrados pelo usuário. Nos dispositivos, acontece o seguinte:
>
> - A configuração de **expiração de senha** é ignorada.
> - Senhas simples, `1111` como ou `1234`, não são permitidas.
> - Um PIN de 6 dígitos é imposto.

- **Palavras-passe simples**: escolha **Bloquear** para exigir palavras-passe mais complexas. **Não configurado** permite palavras-passe simples, tais como `0000` e `1234`.

- **Tipo obrigatório de palavra-passe**: escolha o tipo de palavra-passe exigido pela sua organização. As opções são:
  - **Predefinição do dispositivo**
  - **Numérico**
  - **Alfanumérico**
- **Número de carateres não alfanuméricos na palavra-passe**: especifique o número de caracteres de símbolos, tais como `#` ou `@`, que têm de ser incluídos na palavra-passe.

- **Comprimento mínimo da palavra-passe**: Insira o comprimento mínimo que um usuário deve inserir, entre 4 e 14 caracteres. Em dispositivos registrados pelo usuário, insira um comprimento entre 4 e 6 caracteres.
  
  > [!NOTE]
  > Para dispositivos registrados pelo usuário, os usuários podem definir um PIN maior que 6 dígitos. No entanto, no máximo seis dígitos são impostos no dispositivo. Por exemplo, um administrador define o comprimento mínimo como `8`. Em dispositivos registrados pelo usuário, os usuários só precisam definir um PIN de 6 dígitos. O Intune não força um PIN maior que 6 dígitos em dispositivos registrados pelo usuário.

- **Número de falhas de início de sessão antes de apagar o dispositivo**: Insira o número de entradas com falha a serem permitidas antes que o dispositivo seja apagado (entre 4-11).
  
  o iOS tem segurança interna que pode afetar essa configuração. Por exemplo, o iOS pode atrasar o disparo da política dependendo do número de falhas de entrada. Ele também pode considerar a inserção repetida da mesma senha como uma única tentativa. O [Guia de segurança do IOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) da Apple (abre o site da Apple) é um bom recurso e fornece detalhes mais específicos sobre as senhas.
  
- **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**<sup>1</sup>: introduza o período de tempo durante o qual o dispositivo permanece inativo antes de o utilizador ter de reintroduzir a palavra-passe. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Suportado no iOS 8.0 e em dispositivos mais recentes.
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**<sup>1</sup>: introduza o número máximo de minutos de inatividade permitidos no dispositivo até o ecrã bloquear. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Quando definido como **imediatamente**, a tela é bloqueada com base no tempo mínimo do dispositivo. No iPhone, é de 30 segundos. No iPad, são dois minutos.
- **Expiração da palavra-passe (dias)** : introduza o número de dias antes de ser necessário alterar a palavra-passe do dispositivo.
- **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas para que uma palavra-passe antiga possa ser reutilizada.
- **Bloqueio de ID de toque e ID de face**: Escolha **Bloquear** para impedir o uso de uma impressão digital ou uma face para desbloquear o dispositivo. **Não configurado** permite que o usuário desbloqueie o dispositivo usando esses métodos.

  O bloqueio dessa configuração também impede o uso da autenticação de Faceid para desbloquear o dispositivo.

  A ID de face se aplica a:  
  - iOS 11,0 e mais recente

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Modificação de senha**: escolha **Bloquear** para impedir que o código de acesso seja alterado, adicionado ou removido. As alterações às restrições do código de acesso são ignoradas nos dispositivos supervisionados após o bloqueio desta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.

  - **Modificação de ID de toque e ID de face**: **Bloquear** impede que o usuário altere, adicione ou remova as impressões digitais touchid e a ID facial. **Não configurado** (padrão) permite que o usuário atualize as impressões digitais Touchid e a ID do rosto no dispositivo.

    O bloqueio dessa configuração também impede que o usuário altere, adicione ou remova a autenticação de Faceid.

    A ID de face se aplica a:  
    - iOS 11,0 e mais recente

- **Bloquear Preenchimento Automático de Palavra-passes**: escolha **Bloquear** para impedir a utilização da funcionalidade Preenchimento Automático de Palavras-passe no iOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear pedidos de proximidade de palavra-passe**: escolha **Bloquear** para que o dispositivo de um utilizador não peça palavras-passe aos dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.
- **Bloquear partilha de palavras-passe**: **Bloquear** impede a partilha de palavras-passe entre dispositivos com o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.
- **Exigir a ID de toque ou a autenticação de ID facial para senha ou preenchimento de informações de cartão de crédito**: quando definido como **Exigir**, os utilizadores têm de se autenticar com o Touch ID ou o Face ID para que as palavras-passe ou as informações de cartão de crédito possam ser preenchidas automaticamente no Safari e noutras aplicações. **Não configurado** (predefinição) permite que os utilizadores controlem esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente
  
<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor de ambas as definições para **5** minutos, o ecrã desativa automaticamente passados cinco minutos e o dispositivo bloqueia após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, após o utilizador desativar o ecrã, o dispositivo será bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Acesso ao Centro de Controlo enquanto o dispositivo está bloqueado**: escolha **Bloquear** para impedir o acesso à aplicação do Centro de Controlo enquanto o dispositivo está bloqueado. **Não configurado** (padrão) permite que os usuários acessem o aplicativo do centro de controle quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso às notificações quando o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário acesse as notificações sem desbloquear o dispositivo.
- **Vista Hoje enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso à vista Hoje enquanto o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário veja a exibição atual quando o dispositivo está bloqueado.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Notificações da Carteira enquanto o dispositivo está bloqueado**: **Bloquear** impede o acesso à aplicação Carteira quando o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário acesse o aplicativo de carteira enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Ver documentos empresariais em aplicações não geridas**: **Bloquear** impede a visualização de documentos empresariais em aplicações não geridas. **Não configurado** (padrão) permite que documentos corporativos sejam exibidos em qualquer aplicativo. Por exemplo, quer impedir que os utilizadores guardem os ficheiros da aplicação OneDrive na Dropbox. Configure esta definição como **Bloquear**. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não é permitido guardar.

  - **Permitir que aplicações não geridas leiam a partir de contas com contactos geridas**: Quando definido como **permitir**, os aplicativos não gerenciados, como o aplicativo interno do IOS Contacts, podem ler e acessar informações de contato de aplicativos gerenciados, incluindo o aplicativo móvel do Outlook. **Não configurado** (padrão) impede a leitura, incluindo a remoção de duplicatas, do aplicativo de contatos interno no dispositivo.  
  
    Essa configuração permite ou impede a leitura de informações de contato. Ele não controla a sincronização de contatos entre os aplicativos.
  
    Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

  Para obter mais informações sobre essas duas configurações e seu impacto sobre a sincronização de exportação de contato do Outlook [para IOS, consulte dica de suporte: Use as configurações de perfil personalizado do Intune com o aplicativo](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453)de contatos nativos do Ios.

- **Tratar o AirDrop como um destino não gerido**: **Exigir** força o AirDrop a ser considerado como um destino não gerido. Impede que as aplicações geridas enviem dados através do Airdrop. 
- **Ver documentos não empresariais em aplicações empresariais**: **Bloquear** impede a visualização de documentos não empresariais nas aplicações da empresa. **Não configurado** (padrão) permite que qualquer documento seja exibido em aplicativos gerenciados corporativos.

  A configuração para **Bloquear** também impede a sincronização de exportação de contato no Outlook para Ios. Para obter mais informações, [consulte dica de suporte: Habilitando a sincronização de contatos do iOS do](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453)Outlook com controles de MDM iOS12.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Exigir senha da iTunes Store para todas as compras**: **Exigir** que o usuário insira a senha da ID da Apple para cada compra no aplicativo ou iTunes. **Não configurado** (padrão) permite compras sem solicitar uma senha a cada vez.
- **Compras na aplicação**: escolha **Bloquear** para impedir compras na aplicação na loja. **Não configurado** (padrão) permite a loja de compras em um aplicativo em execução.
- **Transferir conteúdos da iBooks Store sinalizados como “Erótico”** : Escolha **Bloquear** para impedir que os utilizadores transfiram multimédia da iBook Store marcado como “erótico”. **Não configurado** (padrão) permite que o usuário Baixe livros com a categoria "erotismo".
- **Permitir que aplicações geridas escrevam contactos em contas não geridas**: Quando definido como **permitir**, aplicativos gerenciados, como o aplicativo móvel do Outlook, podem salvar ou sincronizar informações de contato, incluindo contatos corporativos e comerciais, para o aplicativo interno de contatos do Ios. Quando definido como **não configurado** (padrão), os aplicativos gerenciados não podem salvar ou sincronizar informações de contato com o aplicativo interno de contatos do Ios no dispositivo.
  
  Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

- **Região das classificações**: escolha a região das classificações que quer utilizar para as transferências permitidas. Em seguida, escolha as classificações permitidas para **filmes**, **programas de TV**e **aplicativos**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **App Store**: **Bloquear** impede o acesso à App Store em dispositivos supervisionados. **Não configurado** (padrão) permite o acesso.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

  - **Instalando aplicativos da App Store**: escolha **Bloquear** para bloquear a App Store no ecrã inicial do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** (padrão) permite a loja de aplicativos na tela inicial.
  - **Downloads automáticos de aplicativos**: escolha **Bloquear** para impedir a transferência automática de aplicações compradas noutros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** (padrão) permite que os aplicativos comprados em outros dispositivos iOS sejam baixados no dispositivo.

- **Conteúdo explícito de música, podcast ou notícias do iTunes**: escolha **Bloquear** para impedir música, podcasts ou notícias de conteúdo explícito no iTunes. **Não configurado** (padrão) permite que o dispositivo acesse o conteúdo classificado como adulto da loja. o iOS 13 e mais recente podem exigir apenas dispositivos supervisionados. 

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Adicionando Game Center amigos**: **Bloquear** impede que os utilizadores adicionem amigos do Game Center. **Não configurado** (padrão) permite que o usuário adicione amigos no Game Center.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Game Center**: **Bloquear** a utilização da aplicação Game Center. **Não configurado** (padrão) permite usar o aplicativo Game Center no dispositivo.
- **Jogos para vários jogadores**: escolha **Bloquear** para impedir jogos de vários jogadores. **Não configurado** (padrão) permite que o usuário Jogue jogos com vários participantes no dispositivo.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Siri**: **Bloquear** impede o acesso à Siri. **Não configurado** (padrão) permite usar o assistente de voz do Siri no dispositivo.
  - **Siri enquanto o dispositivo está bloqueado**: escolha **Bloquear** para impedir o acesso à Siri enquanto o dispositivo está bloqueado. **Não configurado** (padrão) permite usar o assistente de voz do Siri no dispositivo quando ele está bloqueado.

- **Avisos de fraude do Safari**: **Exigir** para que os avisos de fraude sejam mostrados no browser no dispositivo. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Pesquisa de destaque para retornar resultados da Internet**: **Bloquear** impede a pesquisa Spotlight de devolver resultados de uma pesquisa da Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Cookies do Safari**: escolha a forma como os cookies são processados no dispositivo. As opções são:
  - Allow
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual

- **JavaScript do Safari**: **Bloquear** impede que os scripts Java no browser sejam executados no dispositivo. **Não configurado** (padrão) permite scripts java.

- **Pop-ups do Safari**: **Bloquear** para desativar o bloqueador de janelas de pop-up no browser. **Não configurado** (padrão) permite o bloqueador de pop-ups.

- **Registro em log do lado do servidor para comandos Siri**: Quando definido como **desabilitado**, o registro em log de Siri do lado do servidor é desativado. Ele também pode impedir o registro de solicitações de usuário em servidores Siri. **Não configurado** (padrão) registra em log os comandos Siri no lado do servidor. Essa configuração não depende da configuração Siri que está sendo bloqueada ou não configurada.

  Esta funcionalidade aplica-se a:  
  - iOS 12,2 e mais recente

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Câmara**: escolha **Bloquear** para impedir o acesso à câmara no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

  - **FaceTime**: **Bloquear** para impedir o acesso à aplicação FaceTime. **Não configurado** (padrão) permite o acesso ao aplicativo FaceTime no dispositivo.

    A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Filtro de profanação Siri**: **Exigir** impede a Siri de ditar ou dizer palavras ofensivas.

  Para usar essa configuração, defina a configuração **Siri** como **Bloquear**.

- **Siri para consultar o conteúdo gerado pelo usuário da Internet**: **Bloquear** impede a Siri de aceder a sites para responder a perguntas. **Não configurado** (padrão) permite que o Siri acesse o conteúdo gerado pelo usuário da Internet.

  Para usar essa configuração, defina a configuração **Siri** como **Bloquear**.

- **Apple News**: escolha **Bloquear** para impedir o acesso à aplicação Apple News no dispositivo. **Não configurado** (padrão) permite usar o aplicativo Apple News.
- **iBooks Store**: **Bloquear** impede o acesso à iBooks Store. **Não configurado** (padrão) permite que os usuários naveguem e comprem livros da iBooks Store.
- **Aplicativo de mensagens no dispositivo**: **Bloquear** impede que os usuários usem o aplicativo mensagens para IMessage. Se o dispositivo der suporte a mensagens de texto, o usuário ainda poderá enviar e receber mensagens de texto usando o SMS. **Não configurado** (padrão) permite usar o aplicativo mensagens para enviar e ler mensagens pela Internet.
- **Podcasts**: **Bloquear** impede que os utilizadores utilizem a aplicação Podcasts. **Não configurado** (padrão) permite usar o aplicativo podcasts.
- **Serviço de música**: **Bloquear** reverte a aplicação Music para o modo clássico e desativa o Serviço Music. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **serviço iTunes Radio**: **Bloquear** impede que os utilizadores utilizem a aplicação iTunes Radio. **Não configurado** (padrão) permite usar o aplicativo iTunes Radio.
- **iTunes Store**: **Não configurado** (padrão) permite que o iTunes nos dispositivos. **Bloquear** impede que os usuários usem o iTunes no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - iOS 4,0 e mais recente

- **Encontre meu iPhone**: **Não configurado** (padrão) permite usar o recurso Localizar meu aplicativo para obter o local aproximado do dispositivo. **Bloquear** impede esse recurso na localização de meu aplicativo. 

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

- **Encontre meus amigos**: **Não configurado** (padrão) permite usar o recurso Localizar meu aplicativo para encontrar a família e os amigos de um dispositivo Apple ou iCloud.com. **Bloquear** impede esse recurso na localização de meu aplicativo.

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

- **Alterações nas configurações do aplicativo localizar meus amigos**: **Bloquear** impede alterações às definições da aplicação Encontrar Amigos. **Não configurado** (padrão) permite que o usuário altere as configurações para o aplicativo localizar meus amigos.

- **Pesquisa de destaque para retornar resultados da Internet**: **Bloquear** impede a pesquisa Spotlight de devolver resultados de uma pesquisa da Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Bloquear a remoção de aplicativos de sistema do dispositivo**: escolher **Bloquear** desativa a capacidade de remoção de aplicações de sistema do dispositivo. **Não configurado** (padrão) permite que os usuários removam aplicativos do sistema.

- **Safari**: **Bloquear** impede a utilização do browser Safari no dispositivo. **Não configurado** (padrão) permite que os usuários usem o navegador Safari.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Preenchimento automático do Safari**: **Bloquear** desativa a funcionalidade de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Tipo de lista de aplicativos restritos**: Crie uma lista de aplicativos que os usuários não têm permissão para instalar ou usar. As opções são:

  - **Não configurado** (predefinição): Não há restrições do Intune. Os usuários têm acesso aos aplicativos que você atribui e aos aplicativos internos.
  - **Aplicações proibidas**: Aplicativos não gerenciados pelo Intune que você não deseja instalar no dispositivo. Os usuários não são impedidos de instalar um aplicativo proibido. Mas se um usuário instalar um aplicativo dessa lista, ele será relatado no Intune.
  - **Aplicações aprovadas**: Aplicativos que os usuários têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas, se isso for feito, ele será relatado no Intune.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. Por exemplo, para adicionar o aplicativo de pastas de trabalho da `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` Microsoft `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`, digite ou.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou então, **exporte** uma lista existente que inclui a lista de aplicativos restritos no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps"></a>Mostrar ou ocultar aplicações

Aplica-se a dispositivos que executam o iOS 9,3 ou mais recente.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Tipo de lista de aplicativos**: Crie uma lista de aplicativos para mostrar ou ocultar. As opções são:

  - **Aplicações ocultas**: introduza uma lista de aplicações que são ocultadas dos utilizadores. Os utilizadores não podem ver nem abrir estas aplicações.
  - **Aplicações visíveis**: introduza uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

- **URL do aplicativo**: Insira a URL do aplicativo da loja do aplicativo que você deseja mostrar ou ocultar. Por exemplo:

  - Para adicionar o aplicativo de pastas de trabalho da `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` Microsoft `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`, digite ou. 

  - Para adicionar o aplicativo Microsoft Word, digite `https://itunes.apple.com/de/app/microsoft-word/id586447913` ou `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.
  
  Para obter mais informações sobre como localizar uma ID de pacote, consulte [como encontrar a ID de pacote para um aplicativo IOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **ID do pacote da aplicação**: Insira a [ID de lote](bundle-ids-built-in-ios-apps.md) do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Nome da aplicação**: Insira o nome do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Publicador**: Insira o editor do aplicativo desejado.

Para adicionar aplicações, pode:

- **Adicionar**: Selecione para criar sua lista de aplicativos.
- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista de aplicativos restritos que você adicionou, no mesmo formato.

## <a name="wireless"></a>Sem fios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Roaming de dados**: escolha **Bloquear** para impedir o roaming de dados na rede móvel. **Não configurado** (predefinição) permite o roaming de dados quando o dispositivo está numa rede móvel.
- **Obtenção global em segundo plano em roaming**: **Bloquear** impede que seja utilizada a funcionalidade de obtenção global em segundo plano quando estiver a utilizar o roaming na rede móvel. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, como o e-mail, quando estiver a utilizar o roaming numa rede móvel.
- **Marcação por voz**: escolha **Bloquear** para impedir que os utilizadores utilizem a funcionalidade de marcação por voz no dispositivo. **Não configurado** (predefinição) permite a marcação por voz no dispositivo.
- **Chamadas em roaming**: escolha **Bloquear** para impedir as chamadas em roaming na rede móvel. **Não configurado** (predefinição) permite as chamadas em roaming quando o dispositivo está numa rede móvel.
- **Hotspot Pessoal**: **Bloquear** desativa o hotspot pessoal no dispositivo dos utilizadores em cada sincronização do dispositivo. Esta definição poderá não ser compatível com algumas operadoras. **Não configurado** (predefinição) mantém a configuração do hotspot pessoal como o conjunto predefinido pelo utilizador.
- **Regras de utilização de rede móvel (apenas aplicações geridas)** : defina os tipos de dados que as aplicações geridas podem utilizar nas redes móveis. As opções são:
  - **Bloquear a utilização de dados via rede móvel**: bloqueie a utilização de dados via rede móvel para **Todas as aplicações geridas** ou opte por **Escolher aplicações específicas**.
  - **Bloquear a utilização de dados via rede móvel ao efetuar o roaming**: bloqueie a utilização de dados via rede móvel ao utilizar o roaming para **Todas as aplicações geridas** ou opte por **Escolher aplicações específicas**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Alterações nas configurações de uso de dados para celular do aplicativo**: escolha **Bloquear** para impedir as alterações às definições de utilização dos dados via rede móvel da aplicação. **Não configurado** (predefinição) permite que o utilizador controle quais aplicações podem utilizar os dados via rede móvel.
- **Alterações nas configurações do plano celular**: **Bloquear** impede que os utilizadores alterem qualquer definição no plano de dados móveis. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Modificação do usuário de hotspot pessoal**: Quando definido como **Bloquear**, o usuário não pode alterar a configuração de hotspot pessoal. **Não configurado** (padrão) permite que os usuários finais habilitem ou desabilitem seus hotspots pessoais.

  Se você bloquear essa configuração e bloquear a configuração de ponto de interrupção **pessoal** , o hotspot pessoal será desativado.

  Esta funcionalidade aplica-se a:  
  - iOS 12,2 e mais recente

- **Ingresse redes Wi-Fi somente usando perfis de configuração**: **Exigir** força o dispositivo a utilizar apenas as redes Wi-Fi configuradas através de perfis de configuração do Intune. **Não configurado** (predefinição) permite que o dispositivo utilize outras redes Wi-Fi.
- **Modificação do estado de Wi-Fi**: **Não configurado** (padrão) permite que os usuários ativem ou desativem o Wi-Fi no dispositivo. **Bloquear** impede a ativação ou desativação de Wi-Fi.

## <a name="connected-devices"></a>Dispositivos Ligados

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Deteção de pulso para Apple Watch emparelhados**: **Exigir** força um Apple Watch emparelhado a utilizar a deteção de pulso. Quando exigido, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Pedir palavra-passe de emparelhamento para pedidos de saída do AirPlay**: **Exigir** uma palavra-passe de emparelhamento quando o utilizador utiliza o AirPlay para transmitir conteúdo para outros dispositivos da Apple. **Não configurado** (predefinição) permite que o utilizador transmita conteúdo através do AirPlay sem introduzir uma palavra-passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Essoltar**: **Bloquear** impede que o AirDrop seja utilizado no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Emparelhamento de Apple Watch**: **Bloquear** impede o emparelhamento com um Apple Watch. **Não configurado** (predefinição) permite que o dispositivo seja emparelhado com um Apple Watch.
- **Modificação de Bluetooth**: **Bloquear** impede que o utilizador final altere as definições de Bluetooth no dispositivo. **Não configurado** (predefinição) permite que o utilizador altere estas definições.
- **Emparelhamento de host para controlar os dispositivos com os quais um dispositivo IOS pode ser emparelhado**: **Não configurado** (predefinição) permite o emparelhamento de anfitriões para permitir ao administrador controlar os dispositivos com os quais um dispositivo iOS se pode emparelhar. **Bloquear** impede o emparelhamento de anfitriões.
- **Bloquear o esprima**: escolha **Bloquear** para impedir a utilização da funcionalidade AirPrint no dispositivo. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Bloquear o armazenamento de credenciais do esprint no**conjunto de chaves: **Bloquear** impede a utilização do armazenamento Keychain para o nome de utilizador e a palavra-passe no dispositivo. **Não configurado** (predefinição) permite o armazenamento do nome de utilizador e da palavra-passe do AirPrint na aplicação Keychain.
  - **Exigir um certificado TLS confiável para o esprima**: **Exigir** força o dispositivo a utilizar certificados fidedignos para a comunicação de impressão TLS.
  - **Bloquear a descoberta de iBeacon de impressoras de impressão**: **Bloquear** impede que os beacons Bluetooth maliciosos do AirPrint usem phishing no tráfego da rede. **Não configurado** (predefinição) permite a publicidade de impressoras AirPrint no dispositivo.
- **Bloquear a configuração de novos dispositivos próximos**: **Bloquear** desabilita o prompt para configurar novos dispositivos que estão próximos. **Não configurado** (predefinição) permite apresentar avisos aos utilizadores para se ligarem a outros dispositivos Apple próximos.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Pesquisa de definição de palavra**: **Bloquear** impede que o utilizador realce uma palavra e, em seguida, procure a sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Teclados de previsão**: **Não configurado** (padrão) permite usar teclados de previsão para sugerir palavras que o usuário pode querer. **Bloquear** impede esta funcionalidade.
- **Correção automática**: **Não configurado** (padrão) permite que o dispositivo corrija automaticamente palavras incorretas. **Bloquear** impede a utilização da correção automática.
- **Verificação ortográfica do teclado**: **Não configurado** (padrão) permite usar o verificador ortográfico no dispositivo. **Bloquear** não permite a verificação ortográfica.
- **Atalhos de teclado**: **Não configurado** (padrão) permite usar atalhos de teclado no dispositivo. **Bloco** impede o utilizador de utilizar os atalhos de teclado.
- **Ditado**: **Bloquear** impede o utilizador de utilizar entradas de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **QuickPath**: **Não configurado** (padrão) permite que os usuários usem o QuickPath, que permite uma entrada contínua no teclado do dispositivo. Os usuários podem digitar passando o dedo pelas chaves para criar palavras. **Bloquear** impede que os usuários usem o QuickPath. 

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: Todos os tipos de registro

- **Cópia de segurança encriptada**: **Exigir** para que qualquer cópia de segurança seja encriptada.
- **Sincronização das aplicações geridas com a cloud** : **Não configurado** (padrão) permite que seus aplicativos de gerenciamento do Intune sincronizem dados com a conta do iCloud do usuário. **Bloquear** impede esta sincronização de dados com o iCloud.
- **Bloquear Cópias de Segurança dos Livros da Empresa**: escolha **Bloquear** para impedir que os utilizadores façam cópias de segurança dos livros da empresa. **Não configurado** (padrão) permite que os usuários façam backup desses livros.
- **Bloquear a sincronização de metadados dos livros da empresa (notas e destaques)** : **Bloquear** impede a sincronização das notas e dos destaques dos livros da empresa. **Não configurado** (padrão) permite a sincronização.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Sincronização do fluxo de fotografias com o iCloud**: **Não configurado** (padrão) permite que os usuários habilitem **meu fluxo de fotos** em seu dispositivo para sincronizar com o iCloud e ter fotos disponíveis em todos os dispositivos do usuário. **Bloquear** impede a sincronização do fluxo de fotografias com o iCloud. O bloqueio desse recurso pode causar perda de dados. 
- **Fototeca em iCloud**: defina como **Bloquear** para desativar a utilização da fototeca em iCloud para armazenar fotografias e vídeos na cloud. Todas as fotografias que não tiverem sido completamente transferidas da Fototeca em iCloud para o dispositivo serão removidas do dispositivo. **Não configurado** (padrão) permite usar a biblioteca de fotos do iCloud.
- **Fluxo partilhado de fotografias**: escolha **Bloquear** para desativar a **Partilha de Fotografias do iCloud** no dispositivo. **Não configurado** (padrão) permite streaming de fotos compartilhado.
- **Entrega**: **Não configurado** (padrão) permite que os usuários iniciem o trabalho em um dispositivo iOS e, em seguida, continuem o trabalho iniciado em outro dispositivo iOS ou macOS. **Bloquear** impede esta passagem de informações.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Criar cópias de segurança no iCloud**: **Não configurado** (padrão) permite que o usuário faça backup do dispositivo no iCloud. **Bloquear** impede que o utilizador faça cópias de segurança do dispositivo para o iCloud.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Bloquear a sincronização de documentos do icloud**: **Não configurado** (predefinição) permite a sincronização de documentos e pares chave-valor com o espaço de armazenamento do iCloud. **Bloquear** impede o iCloud de sincronizar documentos e dados.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Bloquear sincronização do Keychain com o iCloud**: escolha **Bloquear** para desativar a sincronização das credenciais armazenadas no Keychain com o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

## <a name="autonomous-single-app-mode"></a>Modo de aplicativo único autônomo

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado. Pode executar apenas essa aplicação. Por exemplo, adicione uma aplicação que permita que os utilizadores façam um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Nome da aplicação**: Insira o nome do aplicativo desejado.
- **ID do pacote da aplicação**: Insira a [ID do pacote](bundle-ids-built-in-ios-apps.md) do aplicativo desejado.
- **Adicionar**: Selecione para criar sua lista de aplicativos.

Você também pode **importar** um arquivo CSV com a lista de nomes de aplicativos e suas IDs de pacote. Ou **Exportar** uma lista existente que inclua as aplicações.

## <a name="kiosk"></a>Modo de Local Público

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Aplicação a executar no modo de quiosque**: escolha o tipo de aplicações que quer executar no modo de quiosque. As opções são:
  - **Não configurado** (predefinição): as definições de quiosque não são aplicadas. O dispositivo não é executado no modo de quiosque.
  - **Aplicação da Loja**: introduza o URL para uma aplicação no iTunes App Store.
  - **Aplicação Gerida**: escolha uma aplicação adicionada ao Intune.
  - **Aplicação Incorporada**: Insira a [ID do pacote](bundle-ids-built-in-ios-apps.md) do aplicativo interno.

- **Toque de apoio**: **Exigir** que a definição de acessibilidade Toque de Apoio esteja ativada no dispositivo. Esta funcionalidade ajuda os utilizadores com os gestos no ecrã que podem ser difíceis para eles. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Inverter cores**: **Exigir** a definição de acessibilidade Inverter Cores para que os utilizadores com deficiências visuais possam ajustar o ecrã de visualização. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Áudio mono**: **Exigir** que a definição de acessibilidade Áudio mono esteja ativada no dispositivo. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Controle de voz**: **Exigir** habilita o controle de voz no dispositivo e permite que os usuários controlem totalmente o sistema operacional usando comandos Siri. **Não configurado** desabilita o controle de voz no dispositivo.

  Esta definição aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente
  
  > [!TIP]
  > Se você tiver aplicativos LOB disponíveis para sua organização e eles não estiverem no **controle de voz** pronto no dia 0 quando versões Ios 13,0, recomendamos que você deixe essa configuração como **não configurada**.

- **VoiceOver**: **Exigir** que a definição de acessibilidade VoiceOver esteja ativada no dispositivo para a leitura em voz alta do texto no ecrã. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Zoom**: **Exigir** que a definição Zoom esteja ativada no dispositivo para permitir que os utilizadores utilizem o toque para aumentar o zoom no ecrã. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Bloqueio automático**: **Bloquear** impede o bloqueio automático do dispositivo. **Não configurado** permite esse recurso.
- **Comutador de toque**: **Bloquear** desabilita a opção de toque (mudo) no dispositivo. **Não configurado** permite esse recurso.
- **Rotação do ecrã**: **Bloquear** impede a alteração da orientação da tela quando o usuário gira o dispositivo. **Não configurado** permite esse recurso.
- **Botão de suspensão do ecrã**: Escolha **Bloquear** para desabilitar o botão de ativação de suspensão de tela no dispositivo. **Não configurado** permite esse recurso.
- **Toque**: **Bloquear** desativa o ecrã tátil do dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **Bloquear** impede o uso dos botões de volume no dispositivo. **Não configurado** permite os botões de volume.
- **Controlo de toque de apoio**: **Permitir** permite que os utilizadores utilizem a função de toque de apoio. **Não configurado** desativa esta funcionalidade.
- **Controlo de inversão de cores**: **Permitir** as alterações de inversão de cores para que os utilizadores ajustem a função de inversão de cores. **Não configurado** desativa esta funcionalidade.
- **Falar em texto selecionado**: **Permitir** que as definições de acessibilidade Enunciar Seleção estejam ativadas no dispositivo. Esta funcionalidade lê em voz alta o texto que o utilizador seleciona. **Não configurado** desativa esta funcionalidade.
- **Modificação do controle de voz**: **Permitir que** os usuários alterem o estado do controle de voz em seus dispositivos. **Não configurado** impede que os usuários alterem o estado do controle de voz em seus dispositivos.

  Esta definição aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente

- **Controlo de VoiceOver**: **Permitir** as alterações ao VoiceOver para que os utilizadores atualizem a função VoiceOver, por exemplo, a rapidez com que o texto no ecrã é lido em voz alta. **Não configurado** impede as alterações ao VoiceOver.
- **Controlo de zoom**: **Permitir** as alterações feitas pelo utilizador ao zoom. **Não configurado** impede as alterações ao zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre a utilização da ferramenta Apple Configurator.
> Se a aplicação iOS que introduziu for instalada após a atribuição do perfil, o dispositivo só entrará em modo de quiosque após ser reiniciado.

## <a name="domains"></a>Domínios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Domínios de e-mail não marcados** > **URL do Domínio de E-Mail**: adicione um ou mais URLs à lista. Quando os utilizadores finais receberem um e-mail de um domínio diferentes dos introduzidos, o e-mail será marcado como não fidedigno na aplicação de E-mail do iOS.

- **Domínios Web geridos** > **URL do Domínio Web**: adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzidos, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: Registro de dispositivo automatizado (supervisionado)

- **Domínios de preenchimento automático de palavras-passe do Safari** > **URL do domínio**: adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Essa configuração se aplica somente ao navegador Safari e dispositivos no modo supervisionado. Se você não inserir nenhuma URL, as senhas poderão ser salvas de todos os sites da Web.

  Esta definição aplica-se a:  
  - iOS 9,3 e mais recente

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
>
> - Instalação da aplicação por utilizadores finais
> - Remoção de aplicações
> - FaceTime
> - Safari
> - iTunes
> - Conteúdos explícitos
> - Documentos e dados do iCloud
> - Jogos para vários jogadores
> - Adicionar amigos do Game Center
> - Siri

## <a name="next-steps"></a>Passos seguintes

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [macOS](device-restrictions-macos.md).
