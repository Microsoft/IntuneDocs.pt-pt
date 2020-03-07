---
title: Definições de dispositivos iOS/iPadOS no Microsoft Intune - Azure Microsoft Docs
titleSuffix: ''
description: Adicione, configure ou crie configurações em dispositivos iOS/iPadOS para restringir funcionalidades, incluindo definir requisitos de palavra-passe, controlar o ecrã bloqueado, usar aplicações incorporadas, adicionar aplicações restritas ou aprovadas, lidar com dispositivos Bluetooth, ligar à nuvem para backup e armazenamento, ativar o modo de quiosque, adicionar domínios e controlar como os utilizadores interagem com o navegador web Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86bb9edf96911379631068925315959468f65872
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368984"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos iOS e iPadOS para permitir ou restringir funcionalidades usando Intune

Este artigo lista e descreve as diferentes definições que pode controlar nos dispositivos iOS e iPadOS. Como parte da solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, permitir ou restringir aplicações específicas e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo em Intune e, em seguida, atribuídas ou implantadas para os seus dispositivos iOS/iPadOS.

> [!TIP]
> Estas definições utilizam as definições de MDM da Apple. Para obter mais informações sobre estas definições, consulte [as definições de gestão de dispositivos móveis da Apple](https://support.apple.com/guide/mdm/welcome/web) (abre o site da Apple).

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de restrições do dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Estas configurações aplicam-se a diferentes tipos de matrículas, com algumas definições aplicáveis a todas as opções de inscrição. Para obter mais informações sobre os diferentes tipos de matrículas, consulte a [inscrição do iOS/iPadOS.](../ios-enroll.md)

## <a name="general"></a>Geral

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Partilhar dados de utilização**: Escolha o **Bloco** para evitar que o dispositivo envie dados de diagnóstico e utilização para a Apple. **Não configurado** (predefinição) permite que estes dados sejam enviados.

- **Captura do** **ecrã** : Escolha o Bloco para evitar imagens ou capturas de ecrã no dispositivo. No iOS/iPadOS 9.0 e mais recente, também bloqueia as gravações de ecrã. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Certificados TLS não fidedignos**: Escolha **o bloco** para evitar certificados de segurança de camadas de transporte não confiáveis (TLS) no dispositivo. **Não configurado** (predefinição) permite os certificados TLS.
- **Bloqueie atualizações PKI over-the-air**: **O bloco** impede que os seus utilizadores recebam atualizações de software a menos que o dispositivo esteja ligado a um computador. **Não configurado** (predefinido): permite que um dispositivo receba atualizações de software sem estar ligado a um computador.
- **Limitar o rastreio de anúncios**: Escolha **limite** para desativar o identificador de publicidade do dispositivo. **Não configurado** (predefinição) mantém-no ativado.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Modificação das definições de submissão**de diagnósticos : **O bloco** impede o utilizador de alterar as definições de submissão de diagnóstico e análise de aplicações em **Diagnósticos e Utilizações** (Definições do dispositivo). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

  Para utilizar esta definição, defina a definição de dados de **utilização do Share** para **bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3.2 e mais recente
  - iPadOS 13.0 e mais recente

- **Observação de ecrã remoto por app classroom**: Escolha o **Bloco** para evitar que a aplicação de sala de aula veja remotamente o ecrã no dispositivo. **Não configurado** (predefinição) permite que a aplicação Classroom da Apple veja o ecrã.

  Para utilizar esta definição, defina a definição de captura do **ecrã** para **bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3 e mais recente
  - iPadOS 13.0 e mais recente

- **Observação não solicitada por app classroom**: Se definido para **permitir,** os professores podem observar silenciosamente o ecrã dos dispositivos iOS/iPadOS dos alunos utilizando a app Sala de Aula sem o conhecimento dos alunos. Os dispositivos de estudantes inscritos numa turma através da aplicação Classroom concedem automaticamente permissão ao professor do curso. **Não configurado** (predefinição) impede esta funcionalidade.

  Para utilizar esta definição, defina a definição de captura do **ecrã** para **bloquear**.

- **Enterprise app trust**: Escolha **o Bloco** para remover o botão Trust **Enterprise Developer** em Definições > General > Perfis & Gestão de Dispositivos e Dispositivos no dispositivo. **Não configurado** (predefinição) permite que o utilizador opte por confiar nas aplicações que não são transferidas da App Store.
- **Modificação da conta**: Quando definido para **bloquear,** o utilizador não pode atualizar as definições específicas do dispositivo a partir da aplicação de definições iOS/iPadOS. Por exemplo, o utilizador não pode criar contas novas no dispositivo nem alterar o nome de utilizador ou a palavra-passe. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se também a definições acessíveis a partir da aplicação de definições iOS/iPadOS, tais como Correio, Contactos, Calendário, Twitter e muito mais. Esta funcionalidade não se aplica a apps com configurações de conta que não sejam configuráveis a partir da aplicação de definições iOS/iPadOS, como é o caso da aplicação Microsoft Outlook.

- **Tempo de** **ecrã** : Escolha o Bloco para evitar que os utilizadores estabeleçam as suas próprias restrições no Tempo do Ecrã (definições do dispositivo). **Não configurado** permite que o utilizador configure as restrições do dispositivo (por exemplo, as restrições de acesso ou as restrições de conteúdo e de privacidade) no dispositivo.

  O nome desta definição foi mudado em **Ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 ou mais: **O bloco** impede que os utilizadores finais estabeleçam as suas próprias restrições nas definições do dispositivo. O comportamento é o mesmo; e não existem alterações para os utilizadores finais.
  - iOS 12.0 e mais recente: **O bloco** impede que os utilizadores finais definam o seu próprio Tempo de **Ecrã** nas definições do dispositivo (Definições > General > Tempo de Ecrã), incluindo restrições de conteúdo e privacidade. Os dispositivos atualizados para o iOS 12.0 deixam apresentar o separador de restrições nas definições do dispositivo (Definições > Geral > Gestão de Dispositivos > Perfil de Gestão > Restrições). Estas definições estão em **Tempo do Ecrã**.
  
- **Utilização da opção**de apagar todos os conteúdos e definições no dispositivo : Escolha o **Bloco** para que os utilizadores não possam utilizar todos os conteúdos e definições do dispositivo. **Não configurado** (predefinição) concede aos utilizadores acesso a estas definições.
- **Modificação do nome**do dispositivo : Escolha **o Bloco** para que o nome do dispositivo não possa ser alterado. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Modificação das definições de notificação**: Escolha o **Bloco** para que as definições de notificação não possam ser alteradas. **Não configurado** (predefinição) permite ao utilizador alterar as definições de notificação do dispositivo.
- **Modificação do papel de parede**: O **bloco** impede que o papel de parede seja alterado. **Não configurado** (predefinição) permite ao utilizador alterar a imagem de fundo no dispositivo.
- **Modificação**das definições de confiança da aplicação da empresa : O **bloco** impede o utilizador de alterar as definições de confiança da aplicação da empresa em dispositivos supervisionados. **Não configurado** (predefinição) permite que o utilizador confie nas aplicações que não são transferidas da App Store.
- **Alterações no perfil de configuração**: **O bloco** evita alterações no perfil de configuração no dispositivo. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Bloqueio de ativação**: Escolha **permitir** ativar o bloqueio de ativação em dispositivos iOS/iPadOS supervisionados. O Bloqueio de Ativação dificulta que um dispositivo perdido ou roubado seja reativado.
- **Remoção de aplicativos de bloco**: Escolha **o Bloco** para impedir que os utilizadores removam as aplicações. **Não configurado** (predefinição) permite que os utilizadores removam aplicações do dispositivo.
- **Permitir acessórios USB enquanto o dispositivo estiver bloqueado:** **Permitir que** os acessórios USB troquem dados com um dispositivo que está bloqueado há mais de uma hora. **Não configurado** (predefinido) não atualiza o modo USB Restrito no dispositivo, e os acessórios USB serão bloqueados da transferência de dados do dispositivo se estiverem bloqueados durante mais de uma hora.
- **Forçar a data e a hora automáticas**: **Exigir** forças com controlo de dispositivos para definir automaticamente a Data e a Hora. O fuso horário do dispositivo é atualizado quando o dispositivo está ligado à rede móvel ou ao Wi-Fi com os serviços de localização ativados.
- **Exigir que os alunos solicitem autorização para deixar**o curso de sala de aula : **Exigir** que os alunos matriculados num curso não gerido utilizem a app sala de aula para solicitar autorização ao professor para deixar o curso. **Não configurado** (predefinição) não força o estudante a pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11.3 e mais recente
  - iPadOS 13.0 e mais recente

- Permitir que a **sala de aula bloqueie uma aplicação e bloqueie o dispositivo sem aviso:** **Ativar** permite ao professor bloquear aplicações ou bloquear o dispositivo utilizando a aplicação Sala de aula sem avisar o aluno. Bloquear aplicações significa que o dispositivo pode apenas aceder às aplicações especificadas pelo professor. **Não configurado** (predefinição) impede que os professores bloqueiem aplicações ou dispositivos através da aplicação Classroom sem avisar o estudante.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Junte-se automaticamente às aulas de sala**de aula sem pedir : **Ativar** automaticamente permite que os alunos entrem numa aula que esteja na app de sala de aula sem pedir ao professor. **Não configurado** (predefinição) aviso o professor que os estudantes querem aderir a uma turma da aplicação Classroom.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Criação VPN do bloco**: **O bloco** impede os utilizadores de criar configurações de configuração VPN. **Não configurado** (predefinição) deixa que os utilizadores criem VPNs no dispositivo.
- **Modificação das definições de eSIM**: **O bloco** impede que os utilizadores removam ou adicionem um plano celular ao eSIM do dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12.1 e mais recente
  - iPadOS 13.0 e mais recente

- **Defer atualizações de software**: Quando definido para **Não configurado** (padrão), as atualizações de software são mostradas no dispositivo à medida que a Apple as lança. Por exemplo, se uma atualização iOS/iPadOS for lançada pela Apple numa data específica, então essa atualização aparece naturalmente no dispositivo em torno da data de lançamento.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Adiar a visibilidade das atualizações de software**: Introduza um valor de 0-90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se iOS 12.a estiver disponível a **1 de janeiro** e a opção **Adiar visibilidade** estiver definida como **5 dias**, a iOS 12.a não será mostrado como uma atualização disponível nos dispositivos do utilizador final. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta definição aplica-se a:  
    - iOS 11.3 e mais recente
    - iPadOS 13.0 e mais recente

## <a name="password"></a>Palavra-passe

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Palavra-passe**: **Exija** que o utilizador final introduza uma senha para aceder ao dispositivo. **Não configurado** (predefinido) permite que os utilizadores acedam ao dispositivo sem introduzir uma palavra-passe.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

> [!IMPORTANT]
> Nos dispositivos inscritos pelo utilizador, se configurar qualquer definição de palavra-passe, as definições **de palavras-passe Simples** são automaticamente definidas para **Bloquear**, e um PIN de 6 dígitos é aplicado.
>
> Por exemplo, configura a definição de validade da **Palavra-passe** e empurra esta política para dispositivos inscritos pelo utilizador. Nos dispositivos, acontece o seguinte:
>
> - A definição de expiração da **palavra-passe** é ignorada.
> - Não são permitidas senhas simples, como `1111` ou `1234`.
> - Um pino de 6 dígitos é imposto.

- **Palavras-passe simples**: Escolha **o Bloco** para exigir senhas mais complexas. **Não configurado** permite palavras-passe simples, tais como `0000` e `1234`.

- Tipo de **palavra-passe necessário**: Escolha o tipo de senha que a sua organização necessita. As opções são:
  - **Predefinição do dispositivo**
  - **Numérico**
  - **Alfanumérico**
- **Número de caracteres não alfanuméricos na palavra-passe**: Introduza o número de caracteres de símbolos, tais como `#` ou `@`, que devem ser incluídos na palavra-passe.

- Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo que um utilizador deve introduzir, entre 4 e 14 caracteres. Nos dispositivos inscritos no utilizador, introduza um comprimento entre 4 e 6 caracteres.
  
  > [!NOTE]
  > Para dispositivos inscritos no utilizador, os utilizadores podem definir um PIN superior a 6 dígitos. Mas, não são aplicados mais de 6 dígitos no dispositivo. Por exemplo, um administrador define o comprimento mínimo para `8`. Nos dispositivos inscritos no utilizador, os utilizadores só são obrigados a definir um PIN de 6 dígitos. Intune não força um PIN superior a 6 dígitos em dispositivos matriculados pelo utilizador.

- **Número de falhas de entrada antes de limpar o dispositivo**: Introduza o número de inscrições falhadas para permitir antes de o dispositivo ser limpo (entre 4-11).
  
  O iOS/iPadOS tem uma segurança incorporada que pode afetar esta definição. Por exemplo, o iOS/iPadOS pode atrasar o desencadear da apólice dependendo do número de sinais em falhas. Também pode considerar introduzir repetidamente a mesma senha que uma tentativa. O guia de [segurança iOS/iPadOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) da Apple (abre o site da Apple) é um bom recurso e fornece detalhes mais específicos sobre códigos de acesso.
  
- **Minutos máximos após**o bloqueio do ecrã antes de ser necessária a palavra-passe<sup>1</sup>: Introduza quanto tempo o dispositivo fica inativo antes de o utilizador voltar a introduzir a sua palavra-passe. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Suportado em dispositivos que executam o iOS 8.0+, e iPadOS 13.0+.

- **Minutos máximos de inatividade até que o ecrã bloqueie**<sup>1</sup>: Introduza o número máximo de minutos de inatividade permitidos no aparelho até que o ecrã bloqueie.

  **Opções iOS/iPadOS:**  

  - **Não configurado** (Predefinido): Intune não toca nesta definição.
  - **Imediatamente**: Bloqueios de ecrã após 30 segundos de inatividade.
  - **1**: Bloqueios de ecrã após 1 minuto de inatividade.
  - **2**: Bloqueios de ecrã após 2 minutos de inatividade.
  - **3**: Bloqueios de ecrã após 3 minutos de inatividade.
  - **4**: Bloqueios de ecrã após 4 minutos de inatividade.
  - **5**: Bloqueios de ecrã após 5 minutos de inatividade.

  **opções para iPadOS:**  

  - **Não configurado** (Predefinido): Intune não toca nesta definição.
  - **Imediatamente**: Bloqueios de ecrã após 2 minutos de inatividade.
  - **2**: Bloqueios de ecrã após 2 minutos de inatividade.
  - **5**: Bloqueios de ecrã após 5 minutos de inatividade.
  - **10**: Bloqueios de ecrã após 10 minutos de inatividade.
  - **15**: Bloqueios de ecrã após 15 minutos de inatividade.

  Se um valor não se aplica ao iOS e iPadOS, então a Apple utiliza o valor *mais baixo* mais próximo. Por exemplo, se introduzir `4` minutos, os dispositivos iPadOS usam `2` minutos. Se entrar `10` minutos, os dispositivos iOS utilizam `5` minutos. Esta é uma limitação da Apple.
  
  > [!NOTE]
  > O Intune UI para esta definição não separa os valores suportados pelo iOS e iPadOS. A UI pode ser atualizada num futuro lançamento.

- **Expiração da palavra-passe (dias)** : Introduza o número de dias antes de a palavra-passe do dispositivo ser alterada.
- **Evite a reutilização de senhas anteriores**: Introduza o número de novas palavras-passe que devem ser utilizadas até que uma antiga possa ser reutilizada.
- **Touch ID e Face ID desbloqueie**: Escolha **o Bloco** para evitar a utilização de uma impressão digital ou rosto para desbloquear o dispositivo. O utilizador **não configurado** permite ao utilizador desbloquear o dispositivo utilizando estes métodos.

  Bloquear esta definição também impede a utilização da autenticação FaceID para desbloquear o dispositivo.

  O ID do rosto aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Modificação da senha**: Escolha **o Bloco** para impedir que a senha seja alterada, adicionada ou removida. As alterações às restrições do código de acesso são ignoradas nos dispositivos supervisionados após o bloqueio desta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.

  - **Modificação do ID do toque e do Face ID:** **O bloco** impede o utilizador de alterar, adicionar ou remover as impressões digitais touchID e o Face ID. **Não configurado** (predefinido) permite ao utilizador atualizar as impressões digitais TouchID e o Face ID no dispositivo.

    Bloquear esta definição também impede o utilizador de alterar, adicionar ou remover a autenticação FaceID.

    O ID do rosto aplica-se a:  
    - iOS 11.0 e mais recente
    - iPadOS 13.0 e mais recente

- **Bloquear a palavra-passe AutoFill**: Escolha **o bloco** para evitar a utilização da função de palavras-passe automáticas no iOS/iPadOS. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- Bloqueie pedidos de proximidade de **palavras-passe**: Escolha **o Bloco** para que o dispositivo do utilizador não solicite senhas de dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.
- **Partilha de palavras-passe**bloqueada : **O bloco** impede a partilha de palavras-passe entre dispositivos que utilizam o AirDrop. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.
- **Requerer a autenticação do Touch ID ou face ID para obter informações de palavra-passe ou cartão**de crédito AutoFill : Quando definido para **exigir,** os utilizadores devem autenticar usando touchID ou FaceID antes que palavras-passe ou informações do cartão de crédito possam ser preenchidos automaticamente no Safari e outras aplicações. **Não configurado** (predefinição) permite que os utilizadores controlem esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente
  
<sup>1</sup> Quando configurar os **minutos máximos de inatividade até que** o ecrã bloqueie e **os minutos máximos após** o bloqueio do ecrã antes de ser necessária uma definição de senha, são aplicados em sequência. Por exemplo, se definir o valor de ambas as definições para **5** minutos, o ecrã desativa automaticamente passados cinco minutos e o dispositivo bloqueia após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, após o utilizador desativar o ecrã, o dispositivo será bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Acesso do Centro de Controlo enquanto está bloqueado**pelo dispositivo : Escolha o **Bloco** para impedir o acesso à aplicação Do Centro de Controlo enquanto o dispositivo está bloqueado. **Não configurado** (predefinido) permite aos utilizadores aceder à aplicação Do Control Center quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: O **bloco** impede o acesso às notificações quando o dispositivo está bloqueado. **Não configurado** (predefinido) permite ao utilizador aceder às notificações sem desbloquear o dispositivo.
- **Hoje vista enquanto o dispositivo está bloqueado**: O **bloco** impede o acesso à vista De hoje quando o dispositivo está bloqueado. **Não configurado** (predefinido) permite ao utilizador ver a visualização De hoje quando o dispositivo está bloqueado.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Notificações de carteira enquanto o dispositivo está bloqueado**: O **bloco** impede o acesso à aplicação Wallet quando o dispositivo está bloqueado. **Não configurado** (predefinido) permite ao utilizador aceder à aplicação Wallet enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Visualizar documentos corporativos em aplicações não geridas**: **O Bloco** impede a visualização de documentos corporativos em aplicações não geridas. **Não configurado** (predefinido) permite que documentos corporativos sejam visualizados em qualquer aplicação. Por exemplo, quer impedir que os utilizadores guardem os ficheiros da aplicação OneDrive na Dropbox. Configure esta definição como **Bloquear**. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não é permitido guardar.


  > [!NOTE]
  > Quando esta definição está bloqueada, os teclados de terceiros instalados na App Store também estão bloqueados.

  - **Permitir que as aplicações não geridas leiam**a partir de contas de contactos geridas : Quando definida para **permitir**, aplicações não geridas, como a aplicação incorporada iOS/iPadOS Contacts, podem ler e aceder a informações de contacto de aplicações geridas, incluindo a aplicação móvel Outlook. **Não configurado** (predefinido) impede a leitura, incluindo a remoção de duplicados, da aplicação Contactos incorporados no dispositivo.  
  
    Esta definição permite ou impede a leitura de informações de contacto. Não controla sincronizar contactos entre as aplicações.
  
    Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

  Para obter mais informações sobre estas duas definições e o seu impacto no Outlook para a sincronização de exportação de contactos iOS/iPadOS, consulte [a Dica de Suporte: Utilize as definições de perfil personalizado intune com a aplicação iOS/iPadOS Native Contacts.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453)

- **Trate o AirDrop como um destino não gerido**: **Exigir** que o AirDrop seja considerado um alvo de queda não gerido. Impede que as aplicações geridas enviem dados através do Airdrop. 
- **Visualizar documentos não corporativos em aplicações corporativas**: **O Bloco** impede a visualização de documentos não corporativos em aplicações corporativas. **Não configurado** (padrão) permite que qualquer documento seja visualizado em aplicações geridas por empresas.

  A definição para **bloquear** também impede o contacto com a sincronização de exportação no Outlook para iOS/iPadOS. Para mais informações, consulte [A dica de suporte: Ativar o Outlook iOS/iPadOS Contact Sync com os controlos do MDM iOS12](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Requerer a palavra-passe do iTunes Store para todas as compras**: **Exija** que o utilizador introduza a palavra-passe apple ID para cada compra na aplicação ou iTunes. **Não configurado** (predefinido) permite compras sem pedir sempre uma senha.
- **Compras in-app**: Escolha **o Bloco** para impedir as compras in-app da loja. **Não configurado** (predefinido) permite a compra de loja dentro de uma aplicação de execução.
- **Descarregue os conteúdos da loja iBook sinalizadas como 'Erotica'** : Escolha **o Bloco** para evitar que os utilizadores descarreguem os meios da loja iBook que está marcado como erótica. **Não configurado** (predefinido) permite ao utilizador descarregar livros com a categoria "Erotica".
- **Permitir que as aplicações geridas escrevam contactos para contas**de contactos não geridas : Quando definida para **permitir**, aplicações geridas, como a aplicação móvel Outlook, podem guardar ou sincronizar informações de contacto, incluindo contactos empresariais e corporativos, para a aplicação incorporada iOS/iPadOS Contacts. Quando definido para **Não configurado** (predefinido), as aplicações geridas não podem guardar ou sincronizar informações de contacto para a aplicação de contactos iOS/iPadOS incorporado no dispositivo.
  
  Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

- **Região**de classificações : Escolha a região de classificações que pretende utilizar para downloads permitidos. E depois escolha as classificações permitidas para **Filmes,** **SÉRIEs**de TV e **Apps.**

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Loja de aplicações**: **O bloco** impede o acesso à loja de aplicações em dispositivos supervisionados. **Não configurado** (predefinido) permite o acesso.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

  - **Instalação de aplicações a partir da App Store**: Escolha o **Bloco** para bloquear a loja de aplicações a partir do ecrã principal do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** (predefinido) permite a loja de aplicações no ecrã principal.
  - **Downloads automáticos de aplicações**: Escolha **o Bloco** para evitar o descarregamento automático de aplicações compradas noutros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** (predefinido) permite que as aplicações compradas em outros dispositivos iOS/iPadOS descarreguem no dispositivo.

- Conteúdo explícito da **música, podcast ou notícias**do iTunes : Escolha **o Block** para evitar conteúdos explícitos de música, podcast ou notícias do iTunes. **Não configurado** (predefinido) permite que o dispositivo aceda a conteúdos classificados como adultos a partir da loja.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- **Adicionar amigos do Game Center**: O **Bloco** impede os utilizadores de adicionarem amigos do Game Center. **Não configurado** (predefinido) permite ao utilizador adicionar amigos no Game Center.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- **Game Center**: **Bloqueie** o uso da aplicação Game Center. **Não configurado** (predefinido) permite utilizar a aplicação Game Center no dispositivo.
- **Jogos multijogador**: Escolha **o Bloco** para evitar jogos multijogador. **Não configurado** (predefinido) permite que o utilizador jogue jogos multijogador no dispositivo.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- **Acesso à unidade de rede na aplicação Ficheiros**: Utilizando o protocolo do Bloco de Mensagens do Servidor (SMB), os dispositivos podem aceder a ficheiros ou outros recursos num servidor de rede. **Desativar** impede o acesso a ficheiros numa unidade SMB de rede. **Não configurado** (predefinido) permite o acesso.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Siri**: **Bloco** impede acesso à Siri. **Não configurado** (predefinido) permite utilizar o assistente de voz Siri no dispositivo.
  - **Siri enquanto o dispositivo está bloqueado**: Escolha o **Bloco** para impedir o acesso à Siri quando o dispositivo estiver bloqueado. **Não configurado** (predefinido) permite utilizar o assistente de voz Siri no dispositivo quando está bloqueado.

- **Avisos de fraude safari**: **Exija que** os avisos de fraude sejam mostrados no navegador web do dispositivo. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Pesquisa de holofotes para devolver resultados da internet**: **O Bloco** impede o Spotlight de devolver quaisquer resultados de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Cookies de safari**: Escolha como os cookies são tratados no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual

- **Safari JavaScript**: **Bloco** impede que scripts Java no navegador sejam funcionados no dispositivo. **Não configurado** (padrão) permite scripts Java.

- **Safari Pop-ups**: **Bloqueie** para desativar o bloqueador pop-up no navegador web. **Não configurado** (predefinido) permite o bloqueador pop-up.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Câmara**: Escolha **o Bloco** para impedir o acesso à câmara no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

  - **FaceTime**: **Bloqueie** para impedir o acesso à aplicação FaceTime. **Não configurado** (predefinido) permite o acesso à aplicação FaceTime no dispositivo.

    A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- **Filtro de profanação Siri**: **Exigir** impede a Siri de ditar ou falar linguagem profana.

  Para utilizar esta definição, defina a definição **Siri** para **bloquear**.

- **Siri para consultar conteúdo gerado pelo utilizador a partir da internet**: O **Bloco** impede a Siri de aceder a websites para responder a perguntas. **Não configurado** (predefinido) permite à Siri aceder a conteúdos gerados pelo utilizador a partir da internet.

  Para utilizar esta definição, defina a definição **Siri** para **bloquear**.

- **Apple News**: Escolha **o Bloco** para impedir o acesso à aplicação Apple News no dispositivo. **Não configurado** (padrão) permite usar a aplicação Apple News.
- **loja iBooks**: **Bloco** impede o acesso à loja de iBooks. **Não configurado** (predefinido) permite que os utilizadores naveguem e comprem livros na loja iBooks.
- **Aplicação de mensagens no dispositivo**: **O Bloco** impede os utilizadores de utilizarem a aplicação Mensagens para iMessage. Se o dispositivo suportar mensagens de texto, o utilizador ainda pode enviar e receber mensagens de texto utilizando SMS. **Não configurado** (predefinido) permite utilizar a aplicação Mensagens para enviar e ler mensagens através da internet.
- **Podcasts**: **O bloco** impede os utilizadores de utilizarem a aplicação Podcasts. **Não configurado** (predefinido) permite usar a aplicação Podcasts.
- **Serviço de música**: **O bloco** reverte a aplicação Music para o modo clássico e desativa o serviço De Música. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **serviço de rádio iTunes**: **O bloco** impede os utilizadores de utilizarem a aplicação iTunes Radio. **Não configurado** (predefinido) permite utilizar a aplicação iTunes Radio.
- **loja iTunes**: **Não configurado** (predefinido) permite o iTunes nos dispositivos. **O bloco** impede que os utilizadores utilizem o iTunes no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - iOS 4.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Encontre o meu iPhone**: **Não configurado** (predefinido) permite utilizar esta funcionalidade find My app para obter a localização aproximada do dispositivo. **O Block** impede esta funcionalidade na aplicação Find My. 

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Find my Friends**: **Not configurado** (padrão) permite utilizar esta funcionalidade find My app para encontrar familiares e amigos de um dispositivo Apple ou iCloud.com. **O Block** impede esta funcionalidade na aplicação Find My.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Alterações nas definições da aplicação Find My Friends**: **Block** evita alterações nas definições da aplicação Find My Friends. **Não configurado** (predefinido) permite ao utilizador alterar as definições para a aplicação Find My Friends.

- **Pesquisa de holofotes para devolver resultados da internet**: **O Bloco** impede o Spotlight de devolver quaisquer resultados de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Remoção de blocos de aplicações do sistema a partir do dispositivo**: Escolher o **Bloco** desativa a capacidade de remover aplicações do sistema do dispositivo. **Não configurado** (predefinido) permite que os utilizadores removam as aplicações do sistema.

- **Safari**: **Bloqueie** a utilização do navegador Safari no dispositivo. **Não configurado** (predefinido) permite que os utilizadores utilizem o navegador Safari.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- **Safari Autofill**: **O bloco** desativa a função de enchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Tipo de lista de aplicações restritas**: Criar uma lista de aplicações que os utilizadores não estão autorizados a instalar ou usar. As opções são:

  - **Não configurado** (predefinido): Não existem restrições de Intune. Os utilizadores têm acesso a apps que atribui e aplicações incorporadas.
  - **Aplicações proibidas**: Apps não geridas pela Intune que não deseja instaladas no dispositivo. Os utilizadores não estão impedidos de instalar uma aplicação proibida. Mas se um utilizador instalar uma aplicação a partir desta lista, é reportado no Intune.
  - **Aplicações aprovadas**: Apps que os utilizadores estão autorizados a instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas se o fizerem, é relatado em Intune.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. Por exemplo, para adicionar a aplicação Microsoft Work Folders, insira `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- **Importe** um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou, **Exportar** uma lista existente que inclui a lista de aplicações restritas no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps"></a>Mostrar ou ocultar aplicações

Aplica-se aos dispositivos que executam o iOS 9.3+e iPadOS 13.0+.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Tipo de lista de aplicações**: Criar uma lista de aplicações para mostrar ou ocultar. Você pode mostrar ou esconder aplicativos incorporados e aplicativos de linha de negócio. O site da Apple tem uma lista de [aplicações incorporadas](https://support.apple.com/HT208094)da Apple. As opções são:

  - **Aplicações ocultas**: Insira uma lista de aplicações ocultas dos utilizadores. Os utilizadores não podem ver nem abrir estas aplicações.
  
    A Apple evita esconder algumas aplicações nativas. Por exemplo, não é possível ocultar a aplicação **Definições** no dispositivo. [Eliminar aplicações incorporadas](https://support.apple.com/HT208094) da Apple lista as aplicações que podem ser ocultadas.
  
  - **Aplicativos visíveis**: Insira uma lista de aplicações que os utilizadores possam visualizar e lançar. Mais nenhuma outra aplicação pode ser vista ou lançada.

- **URL da aplicação**: Introduza o URL da aplicação da loja da app que pretende mostrar ou ocultar. Por exemplo:

  - Para adicionar a aplicação Microsoft Work Folders, introduza `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Para adicionar a aplicação Microsoft Word, introduza `https://itunes.apple.com/de/app/microsoft-word/id586447913` ou `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- Id do **pacote de aplicativos**: Introduza o pacote de aplicações [ID](bundle-ids-built-in-ios-apps.md) da app que deseja. Você pode mostrar ou esconder aplicativos incorporados e aplicativos de linha de negócio. O site da Apple tem uma lista de [aplicações incorporadas](https://support.apple.com/HT208094)da Apple.
- Nome da **aplicação**: Introduza o nome da aplicação que deseja. Você pode mostrar ou esconder aplicativos incorporados e aplicativos de linha de negócio. O site da Apple tem uma lista de [aplicações incorporadas](https://support.apple.com/HT208094)da Apple.
- **Editor**: Insira o editor da app que deseja.

Para adicionar aplicações, pode:

- **Adicionar**: Selecione para criar a sua lista de aplicações.
- **Importe** um ficheiro CSV com detalhes sobre a aplicação, incluindo o URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista das aplicações restritas que adicionou, no mesmo formato.

## <a name="wireless"></a>Sem fios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

Nota necessária para roaming de dados (dica ou nota importante para ajudar na confusão do cliente): Esta definição não aparecerá no perfil de gestão do dispositivo direcionado. Isto porque esta definição é tratada como uma ação remota do dispositivo, e cada vez que o estado de roaming de dados é alterado no dispositivo, será novamente bloqueado pelo serviço Intune. Apesar de não estar no perfil de gestão, está a funcionar se mostrar como um sucesso a partir da reportagem na consola de administração. 
- **Roaming de dados**: Escolha **o Bloco** para evitar que os dados perloquem sobre a rede celular. **Não configurado** (predefinição) permite o roaming de dados quando o dispositivo está numa rede móvel.

  > [!IMPORTANT]
  > Esta definição é tratada como uma ação remota do dispositivo. Portanto, esta definição não está mostrada no perfil de gestão do dispositivo. Sempre que o estado de roaming de dados muda no dispositivo, o **roaming de dados** é bloqueado pelo serviço Intune. Em Intune, se o estado de reporte mostrar um sucesso, então saiba que está a funcionar, mesmo que a configuração não seja mostrada no perfil de gestão do dispositivo.

- **Busca**global de fundo durante o roaming : O **bloco** impede a utilização da funcionalidade global de busca de fundo ao roaming através da rede celular. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, como o e-mail, quando estiver a utilizar o roaming numa rede móvel.
- **Marcação por voz**: Escolha **o Bloco** para evitar que os utilizadores utilizem a função de marcação de voz no dispositivo. **Não configurado** (predefinição) permite a marcação por voz no dispositivo.
- **Roaming de voz**: Escolha **o Bloco** para evitar que a voz vagueie sobre a rede celular. **Não configurado** (predefinição) permite as chamadas em roaming quando o dispositivo está numa rede móvel.
- **Hotspot pessoal**: **O bloco** desliga o hotspot pessoal no dispositivo dos utilizadores com cada sincronização do dispositivo. Esta definição pode não ser compatível com algumas transportadoras. **Não configurado** (predefinição) mantém a configuração do hotspot pessoal como o conjunto predefinido pelo utilizador.

  > [!IMPORTANT]
  > Esta definição é tratada como uma ação remota do dispositivo. Portanto, esta definição não está mostrada no perfil de gestão do dispositivo. Sempre que o estado do hotspot pessoal muda no dispositivo, o **Hotspot Pessoal** é bloqueado pelo serviço Intune. Em Intune, se o estado de reporte mostrar um sucesso, então saiba que está a funcionar, mesmo que a configuração não seja mostrada no perfil de gestão do dispositivo.

- Regras de **utilização celular (apenas aplicações geridas)** : Defina os tipos de dados que as aplicações geridas podem usar quando estão em redes celulares. As opções são:
  - **Bloquear a utilização de dados celulares**: Bloquear a utilização de dados celulares para **todas as aplicações geridas** ou **escolher aplicações específicas**.
  - **Bloquear a utilização de dados celulares durante o roaming**: Bloquear a utilização de dados celulares ao roaming para **todas as aplicações geridas** ou **escolher aplicações específicas**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Alterações nas definições de utilização de dados celulares**da aplicação : Escolha **o Bloco** para evitar alterações nas definições de utilização de dados celulares da aplicação. **Não configurado** (predefinição) permite que o utilizador controle quais aplicações podem utilizar os dados via rede móvel.
- **Alterações às definições**do plano celular : **O bloco** impede que os utilizadores mudem quaisquer definições no plano celular. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Modificação do utilizador do Hotspot Pessoal**: Quando definido para **bloquear,** o utilizador não pode alterar a definição de hotspot pessoal. **Não configurado** (predefinido) permite que os utilizadores finais ativem ou desativem o seu hotspot pessoal.

  Se bloquear esta definição e bloquear a definição **de Hotspot Pessoal,** o hotspot pessoal está desligado.

  Esta funcionalidade aplica-se a:  
  - iOS 12.2 e mais recente
  - iPadOS 13.0 e mais recente

- **Junte-se às redes Wi-Fi apenas utilizando perfis**de configuração : **Exija** que o dispositivo utilize apenas redes Wi-Fi configuradas através de perfis de configuração Intune. **Não configurado** (predefinição) permite que o dispositivo utilize outras redes Wi-Fi.

  Quando estiver definido para **exigir,** certifique-se de que o dispositivo tem um perfil Wi-Fi. Se não atribuir um perfil Wi-Fi, esta definição poderá impedir que o dispositivo se ligue à internet. Por outras palavras, se este perfil de restrições do dispositivo for atribuído antes de um perfil Wi-Fi, o dispositivo poderá ser bloqueado da ligação à internet.
  
  Se não conseguir ligar, desinscreva o dispositivo e reinscreva-se com um perfil Wi-Fi. Em seguida, defina esta definição para **exigir** num perfil de restrições do dispositivo e atribua o perfil ao dispositivo.

- **Wi-Fi sempre ligado**: Quando definido para **exigir**, o Wi-Fi permanece ligado na aplicação Definições. Não pode ser desligado em Definições ou no Centro de Controlo, mesmo quando o dispositivo está em modo avião. **Não configurado** (predefinido) permite ao utilizador controlar ligar ou desligar o Wi-Fi.

  Configurar esta definição não impede que os utilizadores selecionem uma rede Wi-Fi.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="connected-devices"></a>Dispositivos Ligados

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Deteção de pulso para relógio Apple emparelhado**: **Exigir** força um relógio Apple emparelhado para usar a deteção do pulso. Quando exigido, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Requerer pedidos de saída do AirPlay a emparelhar palavra-passe**: **Exija** uma palavra-passe de emparelhamento quando o utilizador utilizar o AirPlay para transmitir conteúdo para outros dispositivos da Apple. **Não configurado** (predefinição) permite que o utilizador transmita conteúdo através do AirPlay sem introduzir uma palavra-passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **AirDrop**: **O bloco** evita a utilização do AirDrop no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Emparelhamento Apple Watch**: **Bloco** impede o emparelhamento com um Apple Watch. **Não configurado** (predefinição) permite que o dispositivo seja emparelhado com um Apple Watch.
- **Modificação Bluetooth**: **O bloco** impede o utilizador final de alterar as definições Bluetooth no dispositivo. **Não configurado** (predefinição) permite que o utilizador altere estas definições.
- Emparelhamento de anfitriões para controlar os dispositivos com o qual **um dispositivo iOS/iPadOS pode emparelhar com**: Não **configurado** (padrão) permite o emparelhamento do anfitrião permitir que o administrador controle quais os dispositivos com que um dispositivo iOS/iPadOS pode emparelhar. **Bloquear** impede o emparelhamento de anfitriões.
- **Block AirPrint**: Escolha o **bloco** para evitar a utilização da função AirPrint no dispositivo. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Armazenamento em bloco de credenciais AirPrint no Keychain**: **Bloquear** impede a utilização do armazenamento em keychain para o nome de utilizador e palavra-passe no dispositivo. **Não configurado** (predefinição) permite o armazenamento do nome de utilizador e da palavra-passe do AirPrint na aplicação Keychain.
  - **Requerer um certificado TLS fidedigno para airPrint**: **Exigir** que o dispositivo utilize certificados fidedignos para a comunicação de impressão TLS.
  - Bloquear a **descoberta do iBeacon das impressoras AirPrint**: **Bloco** impede que balizas Bluetooth maliciosas do AirPrint sejam phishing para tráfego de rede. **Não configurado** (predefinição) permite a publicidade de impressoras AirPrint no dispositivo.
- **Bloquear a instalação de novos dispositivos próximos:** **Bloquear** desativa a solicitação para configurar novos dispositivos que se encontram nas proximidades. **Não configurado** (predefinição) permite apresentar avisos aos utilizadores para se ligarem a outros dispositivos Apple próximos.

  Esta funcionalidade aplica-se a:  
  - iOS 11.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Acesso a ficheiros na unidade USB:** Os dispositivos podem ligar e abrir ficheiros numa unidade USB. **Desativar** impede o acesso do dispositivo à unidade USB na aplicação Ficheiros quando uma USB está ligada ao dispositivo. Desativar esta funcionalidade também impede os utilizadores finais de transferirem ficheiros para uma unidade USB ligada a um iPad. **Não configurado** (predefinido) permite o acesso a uma unidade USB na aplicação Ficheiros.

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- Pesquisa de definição de **palavras**: **O bloco** impede o utilizador de realçar uma palavra e, em seguida, procurar a sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Teclados preditivos**: **Não configurado** (predefinido) permite utilizar teclados preditivos para sugerir palavras que o utilizador possa querer. **Bloquear** impede esta funcionalidade.
- **Correção automática**: **Não configurado** (predefinido) permite que o dispositivo corrija automaticamente palavras mal escritas. **Bloquear** impede a utilização da correção automática.
- **Verificação do feitiço**do teclado : **Não configurado** (predefinido) permite utilizar o verificador ortográfico no dispositivo. **Bloquear** não permite a verificação ortográfica.
- **Atalhos de teclado**: **Não configurado** (predefinido) permite utilizar atalhos de teclado no dispositivo. **Bloco** impede o utilizador de utilizar os atalhos de teclado.
- **Ditado**: **O bloco** impede o utilizador de utilizar a entrada de voz para introduzir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **QuickPath**: **Não configurado** (predefinido) permite que os utilizadores utilizem quickPath, o que permite uma entrada contínua no teclado do dispositivo. Os utilizadores podem escrever deslizando através das teclas para criar palavras. **O bloco** impede que os utilizadores utilizem quickPath. 

  Esta funcionalidade aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

### <a name="settings-apply-to-all-enrollment-types"></a>Definições aplicam-se a: Todos os tipos de inscrição

- **Backup encriptado**: **Exija** para que as cópias de segurança do dispositivo sejam encriptadas.
- **As aplicações geridas sincronizam-se na nuvem**: **Não configurado** (padrão) permite que as suas aplicações intune-manages sincronize dados na conta iCloud do utilizador. **Bloquear** impede esta sincronização de dados com o iCloud.
- **Block Enterprise Book Backup**: Escolha **o Bloco** para impedir que os utilizadores apoiem os livros empresariais. **Não configurado** (predefinido) permite que os utilizadores reerque estes livros.
- **Sincronização de metadados de livros empresariais de blocos (notas e destaques)** : **Bloco** impede a sincronização de notas e destaques nos livros empresariais. **Não configurado** (predefinido) permite a sincronização.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Sincronização**de fluxo de fotografia para iCloud : **Não configurado** (padrão) permite que os utilizadores ativem **o My Photo Stream** no seu dispositivo para sincronizar em iCloud, e ter fotos disponíveis em todos os dispositivos do utilizador. **Bloquear** impede a sincronização do fluxo de fotografias com o iCloud. Bloquear esta funcionalidade pode causar perda de dados. 
- **iCloud Photo Library**: Definir para **bloquear** para desativar usando a biblioteca de fotos iCloud para armazenar fotos e vídeos na nuvem. Todas as fotografias que não tiverem sido completamente transferidas da Fototeca em iCloud para o dispositivo serão removidas do dispositivo. **Não configurado** (predefinido) permite utilizar a biblioteca fotográfica iCloud.
- **Fluxo de fotografiapartilhada**: Escolha **o Bloco** para desativar a partilha de fotos do **iCloud** no dispositivo. **Não configurado** (predefinido) permite o streaming de fotografias partilhadas.
- **Entrega**: **Não configurado** (predefinido) permite que os utilizadores comecem a trabalhar num dispositivo iOS/iPadOS e, em seguida, continuem o trabalho que iniciaram noutro dispositivo iOS/iPadOS ou macOS. **Bloquear** impede esta passagem de informações.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Backup para iCloud**: **Não configurado** (predefinido) permite ao utilizador fazer o backup do dispositivo para o iCloud. **Bloquear** impede que o utilizador faça cópias de segurança do dispositivo para o iCloud.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- Bloqueie a sincronização de **documentos do iCloud**: **Não configurado** (predefinido) permite sincronização de documentos e valor-chave para o seu espaço de armazenamento iCloud. **Bloquear** impede o iCloud de sincronizar documentos e dados.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

- Bloqueie a **sincronização do keychain iCloud:** Escolha o **Bloco** para desativar as credenciais de sincronização armazenadas no Keychain para o iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.

  A partir do iOS/iPadOS 13.0, esta definição requer dispositivos supervisionados.

## <a name="autonomous-single-app-mode"></a>Modo de aplicação single autónomo

Utilize estas definições para configurar dispositivos iOS/iPadOS para executar aplicações específicas no modo de aplicação single autónomo. Quando este modo está configurado e o utilizador inicia uma das aplicações configuradas, o dispositivo está bloqueado a essa aplicação. A comutação de aplicações/tarefas é desativada até que o utilizador saia da aplicação permitida.

Por exemplo, em ambiente escolar ou universitário, adicione uma aplicação que permite que os utilizadores possam fazer um teste no dispositivo. Ou, bloqueie o dispositivo na aplicação Portal da Empresa até que o utilizador final se autentique. Quando as ações das aplicações são concluídas pelo utilizador, ou se remove esta política, o dispositivo volta ao seu estado normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- Nome da **aplicação**: Introduza o nome da app que deseja.
- Id do **pacote de aplicativos**: Introduza o [pacote de identificação](bundle-ids-built-in-ios-apps.md) da app que deseja.
- **Adicionar**: Selecione para criar a sua lista de aplicações.

Também pode **importar** um ficheiro CSV com a lista de nomes de aplicações e as suas iDs de pacote. Ou **Exportar** uma lista existente que inclua as aplicações.

## <a name="kiosk"></a>Modo de Local Público

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **App para correr no modo quiosque**: Escolha o tipo de aplicações que pretende executar no modo quiosque. As opções são:
  - **Não configuradas** (predefinidos): As definições do quiosque não são aplicadas. O dispositivo não é executado no modo de quiosque.
  - **App de loja**: Introduza o URL numa aplicação na loja de aplicações do iTunes.
  - **App gerida**: Escolha uma aplicação adicionada ao Intune.
  - **App incorporada**: Introduza o [pacote ID](bundle-ids-built-in-ios-apps.md) da aplicação incorporada.

- **Toque de assistência**: **Exija** que a definição de acessibilidade do Toque de Assistência esteja no dispositivo. Esta funcionalidade ajuda os utilizadores com os gestos no ecrã que podem ser difíceis para eles. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Cores invertas**: **Exija** a definição de acessibilidade invert Colors para que os utilizadores com deficiências visuais possam alterar o ecrã de exibição. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Mono áudio**: **Exija** que a definição de acessibilidade áudio Mono esteja no dispositivo. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Controlo de voz**: **A necessidade** permite o controlo de voz no dispositivo e permite que os utilizadores controlem totalmente o SISTEMA utilizando comandos Siri. **Não configurado desativa** o controlo de voz no dispositivo.

  Esta definição aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente
  
  > [!TIP]
  > Se tiver aplicações LOB disponíveis para a sua organização, e **não** estiverem prontas no dia 0 quando o iOS 13.0 for lançado, recomendamos que deixe esta definição como **Não configurada**.

- **VoiceOver**: **Exija** que a definição de acessibilidade VoiceOver esteja no dispositivo para ler texto no ecrã em voz alta. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Zoom**: **Exija** que a definição de Zoom esteja no dispositivo para que os utilizadores utilizem o toque para ampliar o ecrã. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Bloqueio automático**: **Bloqueio** evita o bloqueio automático do aparelho. **Não configurado** permite esta funcionalidade.
- **Interruptor de toque**: **Bloqueie** o interruptor de toque (mudo) no aparelho. **Não configurado** permite esta funcionalidade.
- **Rotação do ecrã**: **O bloco** evita alterar a orientação do ecrã quando o utilizador roda o dispositivo. **Não configurado** permite esta funcionalidade.
- **Botão de sono de ecrã**: Escolha **bloquear** para desativar o botão de despertar do ecrã no dispositivo. **Não configurado** permite esta funcionalidade.
- **Toque**: **O bloco** desativa o ecrã tátil do dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **Bloquear** evita a utilização dos botões de volume do dispositivo. **Não configurado** permite os botões de volume.
- **Controlo do toque assistida**: **Permitir que** os utilizadores utilizem a função de toque de assistência. **Não configurado** desativa esta funcionalidade.
- **Controlo de cores invertais**: **Permita** alterações de cor inversas para que os utilizadores ajustem a função de cores inversas. **Não configurado** desativa esta funcionalidade.
- **Falar sobre texto selecionado**: **Permita que** as definições de acessibilidade da Seleção de Fala estejam no dispositivo. Esta funcionalidade lê em voz alta o texto que o utilizador seleciona. **Não configurado** desativa esta funcionalidade.
- **Modificação**do controlo de voz : **Permitir que** os utilizadores alterem o estado de controlo de voz nos seus dispositivos. **Não configurado** impede os utilizadores de alterar o estado de controlo de voz nos seus dispositivos.

  Esta definição aplica-se a:  
  - iOS 13.0 e mais recente
  - iPadOS 13.0 e mais recente

- **Controlo VoiceOver**: **Permitir** alterações de voiceover para permitir que os utilizadores atualizem a função VoiceOver, como a rapidez com que o texto no ecrã é lido em voz alta. **Não configurado** impede as alterações ao VoiceOver.
- **Controlo de zoom**: **Permitir** alterações de zoom por parte do utilizador. **Não configurado** impede as alterações ao zoom.

> [!NOTE]
> Antes de configurar um dispositivo iOS/iPadOS para o modo de quiosque, tem de utilizar a ferramenta Configurator apple ou o Programa de Inscrição de Dispositivos apple para colocar o dispositivo em modo supervisionado. Consulte o guia da Apple sobre a utilização da ferramenta Apple Configurator.
> Se a aplicação iOS/iPadOS que introduz estiver instalada depois de atribuir o perfil, o dispositivo não entra no modo quiosque até que o dispositivo seja reiniciado.

## <a name="domains"></a>Domínios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição do dispositivo, inscrição automática de dispositivos (supervisionado)

- **Domínios de e-mail não marcados** > URL de domínio de **e-mail**: Adicione um ou mais URLs à lista. Quando os utilizadores finais recebem um e-mail de um domínio diferente dos domínios em que introduz, o e-mail é marcado como não confiável na aplicação iOS/iPadOS Mail.

- **Domínios Web geridos** > **URL do Domínio Web**: adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzidos, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Definições aplicam-se a: Inscrição automática de dispositivos (supervisionado)

- **Domínios de auto-enchimento de palavra-passe safari** > URL de **domínio:** Adicione um ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Esta definição aplica-se apenas ao navegador Safari e aos dispositivos em modo supervisionado. Se não introduzir urLs, as palavras-passe podem ser guardadas em todos os web sites.

  Esta definição aplica-se a:  
  - iOS 9.3 e mais recente
  - iPadOS 13.0 e mais recente

## <a name="settings-that-require-supervised-mode"></a>Definições que exigem o modo supervisionado

O modo supervisionado iOS/iPadOS só pode ser ativado durante a configuração inicial do dispositivo através do Programa de Inscrição de Dispositivos da Apple, ou utilizando o Configurador Apple. Depois de ativar o modo supervisionado, o Intune pode configurar um dispositivo com a seguinte funcionalidade:

- Bloqueio de Aplicação (Modo de Aplicação Única) 
- Proxy HTTP Global 
- Disable Activation Lock (Desativar o Bloqueio de Ativação) 
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
> - Jogos de vários jogadores
> - Adicionar amigos do Game Center
> - Siri

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [macOS](device-restrictions-macos.md).
