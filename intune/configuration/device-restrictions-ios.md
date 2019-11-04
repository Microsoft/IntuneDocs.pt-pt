---
title: Definições dos dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Adicione, configure ou crie configurações em dispositivos iOS para restringir recursos, incluindo a definição de requisitos de senha, controle a tela bloqueada, use aplicativos internos, adicione aplicativos restritos ou aprovados, manipule dispositivos Bluetooth, conecte-se à nuvem para backup e armazenamento, Habilite o modo de quiosque, adicione domínios e controle como os usuários interagem com o navegador da Web do Safari no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/31/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6dbe26dba4e78e9f5f29a5adedffa3de1df662a6
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414682"
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

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Compartilhar dados de uso**: escolha **Bloquear** para impedir que o dispositivo envie dados de diagnóstico e de uso para a Apple. **Não configurado** (predefinição) permite que estes dados sejam enviados.

- **Captura de tela**: escolha **Bloquear** para impedir capturas de tela ou capturas de telas no dispositivo. No iOS 9,0 e mais recente, ele também bloqueia gravações de tela. **Não configurado** (predefinição) permite ao utilizador capturar o conteúdo do ecrã como uma imagem ou um vídeo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Certificados TLS não confiáveis**: escolha **Bloquear** para impedir certificados de TLS (segurança de camada de transporte) não confiáveis no dispositivo. **Não configurado** (predefinição) permite os certificados TLS.
- **Permitir atualizações de PKI over-the-Air** **: permite que os** usuários recebam atualizações de software sem conectar seus dispositivos a um computador.
- **Limitar o controle do AD**: escolha o **limite** para desabilitar o identificador de publicidade do dispositivo. **Não configurado** (predefinição) mantém-no ativado.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Modificação das configurações de envio de diagnóstico**: o **bloco** impede que o usuário altere as configurações de envio de diagnóstico e análise de aplicativo em **diagnósticos e uso** (configurações do dispositivo). **Não configurado** (predefinição) permite ao utilizador alterar estas definições do dispositivo.

  Para usar essa configuração, defina a configuração **compartilhar dados de uso** como **Bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9.3.2 e mais recente

- **Observação de tela remota por aplicativo de sala de aula**: escolha **Bloquear** para impedir que o aplicativo sala de aula exiba remotamente a tela no dispositivo. **Não configurado** (predefinição) permite que a aplicação Classroom da Apple veja o ecrã.

  Para usar essa configuração, defina a configuração de **captura de tela** como **Bloquear**.

  Esta funcionalidade aplica-se a:  
  - iOS 9,3 e mais recente

- **Observação de tela não solicitada pelo aplicativo sala de aula**: se definido como **permitir**, os professores podem observar silenciosamente a tela de dispositivos IOS dos alunos usando o aplicativo sala de aula sem o conhecimento dos alunos. Os dispositivos de estudantes inscritos numa turma através da aplicação Classroom concedem automaticamente permissão ao professor do curso. **Não configurado** (predefinição) impede esta funcionalidade.

  Para usar essa configuração, defina a configuração de **captura de tela** como **Bloquear**.

- **Confiança do aplicativo empresarial**: escolha o **bloco** para remover o botão de **desenvolvedor corporativo de confiança** nas configurações > perfis de > geral & o gerenciamento de dispositivo no dispositivo. **Não configurado** (predefinição) permite que o utilizador opte por confiar nas aplicações que não são transferidas da App Store.
- **Modificação de conta**: quando definido como **Bloquear**, o usuário não pode atualizar as configurações específicas do dispositivo do aplicativo de configurações do Ios. Por exemplo, o utilizador não pode criar contas novas no dispositivo nem alterar o nome de utilizador ou a palavra-passe. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade também se aplica às definições acessíveis na aplicação de definições do iOS, tais como o Correio, Contactos, Calendário, Twitter e outros. A funcionalidade não se aplica a aplicações com definições da conta que não sejam configuráveis na aplicação de definições do iOS, por exemplo, a aplicação Microsoft Outlook.

- **Hora da tela**: escolha **Bloquear** para impedir que os usuários definam suas próprias restrições no momento da tela (configurações do dispositivo). **Não configurado** permite que o utilizador configure as restrições do dispositivo (por exemplo, as restrições de acesso ou as restrições de conteúdo e de privacidade) no dispositivo.

  O nome desta definição foi mudado em **Ativar restrições nas definições do dispositivo**. Impacto desta alteração:  
  
  - iOS 11.4.1 e anterior: **Bloquear** impede que os usuários finais definam suas próprias restrições nas configurações do dispositivo. O comportamento é o mesmo; e não há nenhuma alteração para os usuários finais.
  - iOS 12,0 e mais recente: **Bloquear** impede que os usuários finais definam seu próprio **tempo de tela** nas configurações do dispositivo (Configurações > Geral > tempo de tela), incluindo restrições de privacidade e conteúdo. Os dispositivos atualizados para o iOS 12.0 deixam apresentar o separador de restrições nas definições do dispositivo (Definições > Geral > Gestão de Dispositivos > Perfil de Gestão > Restrições). Estas definições estão em **Tempo do Ecrã**.
  
- **Uso da opção apagar todo o conteúdo e as configurações no dispositivo**: escolha o **bloco** para que os usuários não possam usar a opção apagar todo o conteúdo e as configurações no dispositivo. **Não configurado** (predefinição) concede aos utilizadores acesso a estas definições.
- **Modificação do nome do dispositivo**: escolha o **bloco** para que o nome do dispositivo não possa ser alterado. **Não configurado** (predefinição) permite ao utilizador alterar o nome do dispositivo.
- **Modificação das configurações de notificação**: escolha **Bloquear** para que as configurações de notificação não possam ser alteradas. **Não configurado** (predefinição) permite ao utilizador alterar as definições de notificação do dispositivo.
- **Modificação de papel de parede**: **bloco** impede que o papel de parede seja alterado. **Não configurado** (predefinição) permite ao utilizador alterar a imagem de fundo no dispositivo.
- **Modificação das configurações de confiança do aplicativo empresarial**: o **bloco** impede que o usuário altere as configurações de confiança do aplicativo empresarial em dispositivos supervisionados. **Não configurado** (predefinição) permite que o utilizador confie nas aplicações que não são transferidas da App Store.
- **Alterações do perfil de configuração**: **Bloquear** impede alterações no perfil de configuração no dispositivo. **Não configurado** (predefinição) permite que o utilizador instale perfis de configuração.
- **Bloqueio de ativação**: escolha **permitir** para habilitar bloqueio de ativação em dispositivos IOS supervisionados. O Bloqueio de Ativação dificulta que um dispositivo perdido ou roubado seja reativado.
- **Bloquear remoção de aplicativo**: escolha **Bloquear** para impedir que os usuários removam aplicativos. **Não configurado** (predefinição) permite que os utilizadores removam aplicações do dispositivo.
- **Bloqueia o modo restrito por USB**: escolha **Bloquear** para desabilitar o modo restrito de USB em dispositivos supervisionados. O modo USB Restricted impede que os acessórios USB mudem de dados com um dispositivo bloqueado por mais de uma hora. **Não configurado** (predefinição) permite o modo USB Restrito.
- **Forçar data e hora automáticas**: **exigir** força dispositivos supervisionados a definir a data & hora automaticamente. O fuso horário do dispositivo é atualizado quando o dispositivo está ligado à rede móvel ou ao Wi-Fi com os serviços de localização ativados.
- **Exigir que os alunos solicitem permissão para sair do curso da sala de aula**: **exigir** força alunos inscritos em um curso não gerenciado usando o aplicativo sala de aula para solicitar permissão do professor para sair do curso. **Não configurado** (predefinição) não força o estudante a pedir permissão.

  Esta funcionalidade aplica-se a:  
  - iOS 11,3 e mais recente

- **Permitir que a sala de aula bloqueie um aplicativo e bloqueie o dispositivo sem avisar**: **habilitar** permite que o professor bloqueie aplicativos ou bloqueie o dispositivo usando o aplicativo sala de aula sem avisar o aluno. Bloquear aplicações significa que o dispositivo pode apenas aceder às aplicações especificadas pelo professor. **Não configurado** (predefinição) impede que os professores bloqueiem aplicações ou dispositivos através da aplicação Classroom sem avisar o estudante.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Unir automaticamente as classes da sala de aula sem avisar**: **habilitar** automaticamente permite que os alunos ingressem em uma classe que esteja no aplicativo da sala de aula sem avisar o professor. **Não configurado** (predefinição) aviso o professor que os estudantes querem aderir a uma turma da aplicação Classroom.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Bloquear a criação de VPN**: **Bloquear** impede que os usuários criem definições de configuração de VPN. **Não configurado** (predefinição) deixa que os utilizadores criem VPNs no dispositivo.
- **Modificando configurações do Esim**: o **bloco** impede que os usuários removam ou adicionem um plano de celular ao Esim no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem estas definições.

  Esta funcionalidade aplica-se a:  
  - iOS 12,1 e mais recente

- **Adiar atualizações de software**: quando definido como **não configurado** (padrão), as atualizações de software são mostradas no dispositivo à medida que a Apple as libera. Por exemplo, se uma atualização do iOS for lançada pela Apple numa data específica, essa atualização será mostrada naturalmente no dispositivo por volta da data de lançamento.

  **Ativar** permite-lhe adiar a apresentação das atualizações de software nos dispositivos, entre 0 e 90 dias. Esta definição não controla quando as atualizações são ou não instaladas. 

  - **Atrasar a visibilidade das atualizações de software**: Insira um valor de 0-90 dias. Quando o adiamento expirar, os utilizadores recebem uma notificação para atualizar para a versão mais antiga do SO disponível quando o adiamento foi acionado.

    Por exemplo, se iOS 12.a estiver disponível a **1 de janeiro** e a opção **Adiar visibilidade** estiver definida como **5 dias**, a iOS 12.a não será mostrado como uma atualização disponível nos dispositivos do utilizador final. No **sexto dia** após o lançamento, essa atualização estará disponível e os utilizadores finais poderão instalá-la.

    Esta definição aplica-se a:  
    - iOS 11,3 e mais recente

## <a name="password"></a>Palavra-passe

> [!NOTE]
> Em uma versão futura, essas configurações de senha na interface do usuário do Intune estão sendo atualizadas para corresponder ao tipo de registro.

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Senha**: **exige** que o usuário final Insira uma senha para acessar o dispositivo. **Não configurado** (padrão) permite que os usuários acessem o dispositivo sem inserir uma senha.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

> [!IMPORTANT]
> Em dispositivos registrados pelo usuário, se você definir qualquer configuração de senha, as configurações de **senhas simples** serão automaticamente definidas como **Bloquear**e um PIN de 6 dígitos será imposto.
>
> Por exemplo, você define a configuração de **expiração de senha** e envia por push essa política para dispositivos registrados pelo usuário. Nos dispositivos, acontece o seguinte:
>
> - A configuração de **expiração de senha** é ignorada.
> - Senhas simples, como `1111` ou `1234`, não são permitidas.
> - Um PIN de 6 dígitos é imposto.

- **Senhas simples**: escolha **Bloquear** para exigir senhas mais complexas. **Não configurado** permite palavras-passe simples, tais como `0000` e `1234`.

- **Tipo de senha necessária**: escolha o tipo de senha que sua organização precisa. As opções são:
  - **Predefinição do dispositivo**
  - **Numérico**
  - **Alfanumérico**
- **Número de caracteres não alfanuméricos na senha**: Insira o número de caracteres de símbolo, como `#` ou `@`, que deve ser incluído na senha.

- **Comprimento mínimo da senha**: Insira o comprimento mínimo que um usuário deve inserir, entre 4 e 14 caracteres. Em dispositivos registrados pelo usuário, insira um comprimento entre 4 e 6 caracteres.
  
  > [!NOTE]
  > Para dispositivos registrados pelo usuário, os usuários podem definir um PIN maior que 6 dígitos. No entanto, no máximo seis dígitos são impostos no dispositivo. Por exemplo, um administrador define o comprimento mínimo como `8`. Em dispositivos registrados pelo usuário, os usuários só precisam definir um PIN de 6 dígitos. O Intune não força um PIN maior que 6 dígitos em dispositivos registrados pelo usuário.

- **Número de falhas de entrada antes de apagar o dispositivo**: Insira o número de entradas com falha a serem permitidas antes que o dispositivo seja apagado (entre 4-11).
  
  o iOS tem segurança interna que pode afetar essa configuração. Por exemplo, o iOS pode atrasar o disparo da política dependendo do número de falhas de entrada. Ele também pode considerar a inserção repetida da mesma senha como uma única tentativa. O [Guia de segurança do IOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) da Apple (abre o site da Apple) é um bom recurso e fornece detalhes mais específicos sobre as senhas.
  
- **Máximo de minutos após o bloqueio de tela antes que a senha seja necessária**<sup>1</sup>: Insira por quanto tempo o dispositivo permanece ocioso antes de o usuário precisar digitar novamente sua senha. Se o tempo introduzido for maior do que o valor definido no dispositivo, o dispositivo ignorará o tempo introduzido. Suportado no iOS 8.0 e em dispositivos mais recentes.

- **Máximo de minutos de inatividade até a tela travar**<sup>1</sup>: Insira o número máximo de minutos de inatividade permitido no dispositivo até que a tela seja bloqueada.

  **Opções do IOS**:  

  - **Não configurado** (padrão): o Intune não toca nessa configuração.
  - **Imediatamente**: bloqueios de tela após 30 segundos de inatividade.
  - **1**: bloqueios de tela após 1 minuto de inatividade.
  - **2**: bloqueios de tela após 2 minutos de inatividade.
  - **3**: bloqueios de tela após 3 minutos de inatividade.
  - **4**: bloqueios de tela após 4 minutos de inatividade.
  - **5**: bloqueios de tela após 5 minutos de inatividade.
    
  **Opções de iPadOS**:  

  - **Não configurado** (padrão): o Intune não toca nessa configuração.
  - **Imediatamente**: a tela é bloqueada após 2 minutos de inatividade.
  - **2**: bloqueios de tela após 2 minutos de inatividade.
  - **5**: bloqueios de tela após 5 minutos de inatividade.
  - **10**: bloqueios de tela após 10 minutos de inatividade.
  - **15**: bloqueios de tela após 15 minutos de inatividade.

  Se um valor não se aplicar ao iOS ou iPadOS, a Apple usará o *menor valor mais* próximo. Por exemplo, se você inserir `4` minutos, os dispositivos iPadOS usarão `2` minutos. Se você inserir `10` minutos, os dispositivos iOS usarão `5` minutos. Essa é uma limitação da Apple.
  
  > [!NOTE]
  > A interface do usuário do Intune para essa configuração não separa os valores com suporte para iOS e iPadOS. A interface do usuário pode ser atualizada em uma versão futura.

- **Expiração da senha (dias)** : Insira o número de dias antes que a senha do dispositivo deva ser alterada.
- **Evitar a reutilização de senhas anteriores**: Insira o número de novas senhas que devem ser usadas até que uma antiga possa ser reutilizada.
- **ID de toque e desbloqueio de ID facial**: escolha **Bloquear** para impedir o uso de uma impressão digital ou uma face para desbloquear o dispositivo. **Não configurado** permite que o usuário desbloqueie o dispositivo usando esses métodos.

  O bloqueio dessa configuração também impede o uso da autenticação de Faceid para desbloquear o dispositivo.

  A ID de face se aplica a:  
  - iOS 11,0 e mais recente

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Modificação de senha**: escolha o **bloco** para impedir que a senha seja alterada, adicionada ou removida. As alterações às restrições do código de acesso são ignoradas nos dispositivos supervisionados após o bloqueio desta funcionalidade. **Não configurado** (predefinição) permite que os códigos de acesso sejam adicionados, alterados ou removidos.

  - **Modificação de ID de toque e ID de face**: o **bloco** impede que o usuário altere, adicione ou remova as impressões digitais Touchid e a ID facial. **Não configurado** (padrão) permite que o usuário atualize as impressões digitais touchid e a ID do rosto no dispositivo.

    O bloqueio dessa configuração também impede que o usuário altere, adicione ou remova a autenticação de Faceid.

    A ID de face se aplica a:  
    - iOS 11,0 e mais recente

- **Bloquear AutoPreenchimento de senha**: escolha **Bloquear** para impedir o uso do recurso de senhas de preenchimento automático no Ios. A escolha de **Bloquear** também tem o seguinte impacto:

  - Não é pedido aos utilizadores que utilizem uma palavra-passe guardada no Safari nem noutras aplicações.
  - As Palavras-passe Seguras automáticas estão desativadas, pelo que não são sugeridas aos utilizadores.

  **Não configurado** (predefinição) permite estas funcionalidades.

- **Bloquear solicitações de proximidade de senha**: escolha **Bloquear** para que o dispositivo de um usuário não solicite senhas de dispositivos próximos. **Não configurado** (predefinição) permite estes pedidos de palavras-passe.
- **Bloquear o compartilhamento de senha**: **Bloquear** impede o compartilhamento de senhas entre dispositivos usando o essoltar. **Não configurado** (predefinição) permite que as palavras-passe sejam partilhadas.
- **Exigir a ID de toque ou a autenticação de ID facial para senha ou preenchimento de informações de cartão de crédito**: quando definido como **exigir**, os usuários devem autenticar usando touchid ou faceid antes que as senhas ou as informações de cartão de crédito possam ser preenchidas automaticamente no Safari e em outras os. **Não configurado** (predefinição) permite que os utilizadores controlem esta funcionalidade nas definições do dispositivo.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente
  
<sup>1</sup>Quando configura as definições **Máximo de minutos de inatividade até o ecrã ser bloqueado** e **Máximo de minutos após o bloqueio de ecrã antes de ser exigida a palavra-passe**, estas são aplicadas em sequência. Por exemplo, se definir o valor de ambas as definições para **5** minutos, o ecrã desativa automaticamente passados cinco minutos e o dispositivo bloqueia após mais cinco minutos. No entanto, se o utilizador desligar o ecrã manualmente, a segunda definição será imediatamente aplicada. No mesmo exemplo, após o utilizador desativar o ecrã, o dispositivo será bloqueado passados cinco minutos.

## <a name="locked-screen-experience"></a>Experiência de Ecrã Bloqueado

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Acesso ao centro de controle enquanto o dispositivo está bloqueado**: escolha **Bloquear** para impedir o acesso ao aplicativo do centro de controle enquanto o dispositivo estiver bloqueado. **Não configurado** (padrão) permite que os usuários acessem o aplicativo do centro de controle quando o dispositivo está bloqueado.
- **Notificações enquanto o dispositivo está bloqueado**: o **bloqueio** impede o acesso a notificações quando o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário acesse as notificações sem desbloquear o dispositivo.
- **Exibição atual enquanto o dispositivo está bloqueado**: o **bloqueio** impede o acesso à exibição atual quando o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário veja a exibição atual quando o dispositivo está bloqueado.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Notificações de carteira enquanto o dispositivo estiver bloqueado**: **Bloquear** impede o acesso ao aplicativo de carteira quando o dispositivo está bloqueado. **Não configurado** (padrão) permite que o usuário acesse o aplicativo de carteira enquanto o dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Visualização de Documentos, Jogos

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Exibindo documentos corporativos em aplicativos não gerenciados**: o **bloco** impede a exibição de documentos corporativos em aplicativos não gerenciados. **Não configurado** (padrão) permite que os documentos corporativos sejam exibidos em qualquer aplicativo. Por exemplo, quer impedir que os utilizadores guardem os ficheiros da aplicação OneDrive na Dropbox. Configure esta definição como **Bloquear**. Depois de o dispositivo receber a política (por exemplo, após um reinício), já não é permitido guardar.

  - **Permitir que aplicativos não gerenciados leiam de contas de contatos gerenciados**: quando definido como **permitir**, aplicativos não gerenciados, como o aplicativo interno do IOS Contacts, podem ler e acessar informações de contato de aplicativos gerenciados, incluindo o aplicativo móvel do Outlook. **Não configurado** (padrão) impede a leitura, incluindo a remoção de duplicatas, do aplicativo de contatos interno no dispositivo.  
  
    Essa configuração permite ou impede a leitura de informações de contato. Ele não controla a sincronização de contatos entre os aplicativos.
  
    Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

  Para obter mais informações sobre essas duas configurações e seu impacto sobre a sincronização de exportação de contato do Outlook para iOS, consulte [dica de suporte: usar configurações de perfil personalizado do Intune com o aplicativo de contatos nativos do IOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Tratar o essoltar como um destino não gerenciado**: **exigir** que o esforce seja considerado um destino de soltura não gerenciado. Impede que as aplicações geridas enviem dados através do Airdrop. 
- **Exibindo documentos não corporativos em aplicativos corporativos**: o **bloco** impede a exibição de documentos não corporativos em aplicativos corporativos. **Não configurado** (padrão) permite que qualquer documento seja exibido em aplicativos gerenciados corporativos.

  A configuração para **Bloquear** também impede a sincronização de exportação de contato no Outlook para Ios. Para obter mais informações, consulte [dica de suporte: Habilitando a sincronização de contatos do Outlook Ios com controles de MDM iOS12](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Exigir senha da iTunes Store para todas as compras**: **exige** que o usuário insira a senha da ID da Apple para cada compra no aplicativo ou iTunes. **Não configurado** (padrão) permite compras sem solicitar uma senha a cada vez.
- **Compras no aplicativo**: escolha **Bloquear** para evitar compras no aplicativo da loja. **Não configurado** (padrão) permite a loja de compras em um aplicativo em execução.
- **Baixar conteúdo da iBook Store sinalizado como ' erotismo '** : escolha **Bloquear** para impedir que os usuários baixem mídia da iBook Store marcada como erotismo. **Não configurado** (padrão) permite que o usuário Baixe livros com a categoria "erotismo".
- **Permitir que aplicativos gerenciados gravem contatos em contas de contatos não gerenciados**: quando definido como **permitir**, aplicativos gerenciados, como o aplicativo móvel do Outlook, podem salvar ou sincronizar informações de contato, incluindo contatos comerciais e corporativos, para os contatos internos do IOS aplicação. Quando definido como **não configurado** (padrão), os aplicativos gerenciados não podem salvar ou sincronizar informações de contato com o aplicativo interno de contatos do Ios no dispositivo.
  
  Para utilizar esta definição, configure **Ver documentos empresariais em aplicações não geridas** como **Bloquear**.

- **Região de classificações**: escolha a região de classificações que você deseja usar para downloads permitidos. Em seguida, escolha as classificações permitidas para **filmes**, **programas de TV**e **aplicativos**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **App Store**: o **bloco** impede o acesso à loja de aplicativos em dispositivos supervisionados. **Não configurado** (padrão) permite o acesso.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

  - **Instalando aplicativos da App Store**: escolha **Bloquear** para bloquear a loja de aplicativos na tela inicial do dispositivo. Os utilizadores finais podem continuar a utilizar o iTunes ou o Apple Configurator para instalar aplicações. **Não configurado** (padrão) permite a loja de aplicativos na tela inicial.
  - **Downloads automáticos de aplicativos**: escolha **Bloquear** para impedir o download automático de aplicativos comprados em outros dispositivos. Não afeta a atualização das aplicações existentes. **Não configurado** (padrão) permite que os aplicativos comprados em outros dispositivos IOS sejam baixados no dispositivo.

- **Conteúdo explícito de música, podcast ou notícias do iTunes**: escolha **Bloquear** para evitar conteúdo explícito de música, podcast ou notícias do iTunes. **Não configurado** (padrão) permite que o dispositivo acesse o conteúdo classificado como adulto da loja. o iOS 13 e mais recente podem exigir apenas dispositivos supervisionados. 

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Adicionar Game Center amigos**: **Bloquear** impede que os usuários adicionem Game Center amigos. **Não configurado** (padrão) permite que o usuário adicione amigos em Game Center.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Game Center**: **Bloquear** o uso do aplicativo Game Center. **Não configurado** (padrão) permite usar o aplicativo Game Center no dispositivo.
- **Jogos para vários jogadores**: escolha **Bloquear** para evitar jogos com vários participantes. **Não configurado** (padrão) permite que o usuário Jogue jogos com vários participantes no dispositivo.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Acesso à unidade de rede no aplicativo de arquivos**: usando o protocolo SMB, os dispositivos podem acessar arquivos ou outros recursos em um servidor de rede. **Desabilitar** impede o acesso a arquivos em uma unidade SMB de rede. **Não configurado** (padrão) permite o acesso.

  Esta funcionalidade aplica-se a:  
  - iOS e iPadOS 13,0 e mais recentes

## <a name="built-in-apps"></a>Aplicações Incorporadas

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Siri**: **Block** impede o acesso ao Siri. **Não configurado** (padrão) permite usar o assistente de voz Siri no dispositivo.
  - **Siri enquanto o dispositivo estiver bloqueado**: escolha **Bloquear** para impedir o acesso ao Siri quando o dispositivo estiver bloqueado. **Não configurado** (padrão) permite usar o assistente de voz Siri no dispositivo quando ele está bloqueado.

- **Avisos de fraude do Safari**: **exigir** que avisos de fraude sejam mostrados no navegador da Web no dispositivo. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **A pesquisa de destaque para retornar resultados da Internet**: **Bloquear** impede que o Spotlight retorne qualquer resultado de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Cookies do Safari**: escolha como os cookies são manipulados no dispositivo. As opções são:
  - Permitir
  - Bloquear todos os cookies
  - Permitir cookies dos sites visitados
  - Permitir cookies do site atual

- **Safari JavaScript**: **Block** impede que scripts java no navegador sejam executados no dispositivo. **Não configurado** (padrão) permite scripts java.

- **Pop-ups do Safari**: **Bloquear** para desabilitar o bloqueador de pop-ups no navegador da Web. **Não configurado** (padrão) permite o bloqueador de pop-ups.

- **Registro em log do lado do servidor para comandos Siri**: quando definido como **desabilitado**, o registro em log de Siri do servidor é desativado. Ele também pode impedir o registro de solicitações de usuário em servidores Siri. **Não configurado** (padrão) registra os comandos Siri no lado do servidor. Essa configuração não depende da configuração Siri que está sendo bloqueada ou não configurada.

  Esta funcionalidade aplica-se a:  
  - iOS 12,2 e mais recente

  > [!NOTE]
  > A configuração **log do lado do servidor para comandos Siri** é preterida pela Apple. Em uma versão futura, essa configuração é removida do console do Intune.
  >
  > Atualmente, essa configuração não tem nenhum efeito nos dispositivos, mesmo que a configuração seja mostrada nos perfis gerenciamento dispositivos. Para excluir essa configuração de qualquer política, abra a política, faça uma alteração secundária e, em seguida, salve a política. A política é atualizada e a configuração é excluída dos dispositivos.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Câmera**: escolha **Bloquear** para impedir o acesso à câmera no dispositivo. **Não configurado** (predefinição) permite o acesso à câmara do dispositivo.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

  - **FaceTime**: **Bloquear** para impedir o acesso ao aplicativo FaceTime. **Não configurado** (padrão) permite o acesso ao aplicativo FaceTime no dispositivo.

    A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Filtro de profanação Siri**: **exigir** que o Siri dite ou fale com linguagem obscena.

  Para usar essa configuração, defina a configuração **Siri** como **Bloquear**.

- **Siri para consultar o conteúdo gerado pelo usuário da Internet**: **Bloquear** impede que o Siri acesse sites para responder a perguntas. **Não configurado** (padrão) permite que o Siri acesse o conteúdo gerado pelo usuário da Internet.

  Para usar essa configuração, defina a configuração **Siri** como **Bloquear**.

- **Apple News**: escolha **Bloquear** para impedir o acesso ao aplicativo Apple News no dispositivo. **Não configurado** (padrão) permite usar o aplicativo Apple News.
- **iBooks Store**: **Block** impede o acesso ao armazenamento do iBooks. **Não configurado** (padrão) permite que os usuários naveguem e comprem livros da iBooks Store.
- **Aplicativo de mensagens no dispositivo**: **Bloquear** impede que os usuários usem o aplicativo mensagens para IMessage. Se o dispositivo der suporte a mensagens de texto, o usuário ainda poderá enviar e receber mensagens de texto usando o SMS. **Não configurado** (padrão) permite usar o aplicativo mensagens para enviar e ler mensagens pela Internet.
- **Podcasts**: **Bloquear** impede que os usuários usem o aplicativo podcasts. **Não configurado** (padrão) permite usar o aplicativo podcasts.
- **Serviço de música**: o **bloco** reverte o aplicativo de música para o modo clássico e desabilita o serviço de música. **Não configurado** (predefinição) permite a utilização da aplicação Apple Music.
- **serviço iTunes Radio**: **Bloquear** impede que os usuários usem o aplicativo iTunes Radio. **Não configurado** (padrão) permite usar o aplicativo iTunes Radio.
- **iTunes Store**: **não configurado** (padrão) permite o iTunes nos dispositivos. **Bloquear** impede que os usuários usem o iTunes no dispositivo. 

  Esta funcionalidade aplica-se a:  
  - iOS 4,0 e mais recente

- **Localizar meu iPhone**: **não configurado** (padrão) permite usar o recurso Localizar meu aplicativo para obter o local aproximado do dispositivo. **Bloquear** impede esse recurso na localização de meu aplicativo. 

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

- **Localizar meus amigos**: **não configurado** (padrão) permite usar o recurso Localizar meu aplicativo para encontrar a família e os amigos de um dispositivo Apple ou icloud.com. **Bloquear** impede esse recurso na localização de meu aplicativo.

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

- **Alterações nas configurações do aplicativo localizar meus amigos**: **Bloquear** impede alterações nas configurações do aplicativo localizar meus amigos. **Não configurado** (padrão) permite que o usuário altere as configurações para o aplicativo localizar meus amigos.

- **A pesquisa de destaque para retornar resultados da Internet**: **Bloquear** impede que o Spotlight retorne qualquer resultado de uma pesquisa na Internet. **Não configurado** (predefinição) permite que o Spotlight se ligue à Internet para fornecer resultados da pesquisa.

- **Bloquear a remoção de aplicativos do sistema do dispositivo**: escolher **bloco** desabilita a capacidade de remover aplicativos do sistema do dispositivo. **Não configurado** (padrão) permite que os usuários removam aplicativos do sistema.

- **Safari**: **Bloquear** usando o navegador Safari no dispositivo. **Não configurado** (padrão) permite que os usuários usem o navegador Safari.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Preenchimento automático do Safari**: o **bloco** desabilita o recurso de preenchimento automático no Safari no dispositivo. **Não configurado** (predefinição) permite que os utilizadores alterem as definições de preenchimento automático no browser.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

## <a name="restricted-apps"></a>Aplicações restritas

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Tipo de lista de aplicativos restritos**: Crie uma lista de aplicativos que os usuários não têm permissão para instalar ou usar. As opções são:

  - **Não configurado** (padrão): não há restrições do Intune. Os usuários têm acesso aos aplicativos que você atribui e aos aplicativos internos.
  - **Aplicativos proibidos**: aplicativos não gerenciados pelo Intune que você não deseja instalar no dispositivo. Os usuários não são impedidos de instalar um aplicativo proibido. Mas se um usuário instalar um aplicativo dessa lista, ele será relatado no Intune.
  - **Aplicativos aprovados**: aplicativos que os usuários têm permissão para instalar. Os utilizadores não podem instalar aplicações que não estejam listadas. As aplicações geridas pelo Intune são automaticamente permitidas. Os utilizadores não são impedidos de instalar uma aplicação que não esteja na lista aprovada. Mas, se isso for feito, ele será relatado no Intune.

Para adicionar aplicações a estas listas, pode:

- **Adicionar** o URL do iTunes App Store da aplicação desejada. Por exemplo, para adicionar o aplicativo de pastas de trabalho da Microsoft, digite `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.

- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou então, **exporte** uma lista existente que inclui a lista de aplicativos restritos no mesmo formato.

> [!IMPORTANT]
> Os perfis de dispositivo que utilizam as definições de aplicações restritas têm de ser atribuídos a grupos de utilizadores.

## <a name="show-or-hide-apps"></a>Mostrar ou ocultar aplicações

Aplica-se a dispositivos que executam o iOS 9,3 ou mais recente.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Tipo de lista de aplicativos**: Crie uma lista de aplicativos para mostrar ou ocultar. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094). As opções são:

  - **Aplicativos ocultos**: Insira uma lista de aplicativos que estão ocultos dos usuários. Os utilizadores não podem ver nem abrir estas aplicações.
  - **Aplicativos visíveis**: Insira uma lista de aplicativos que os usuários podem exibir e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

- **URL do aplicativo**: Insira a URL do aplicativo da loja do aplicativo que você deseja mostrar ou ocultar. Por exemplo:

  - Para adicionar o aplicativo de pastas de trabalho da Microsoft, digite `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Para adicionar o aplicativo Microsoft Word, digite `https://itunes.apple.com/de/app/microsoft-word/id586447913` ou `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Para localizar o URL de uma aplicação, abra o iTunes App Store e procure a aplicação. Por exemplo, procure `Microsoft Remote Desktop` ou `Microsoft Word`. Selecione a aplicação e copie o URL.

  Também pode utilizar o iTunes para localizar a aplicação e, em seguida, utilizar a tarefa **Copiar Ligação** para obter o URL da aplicação.
  
  Para obter mais informações sobre como localizar uma ID de pacote, consulte [como encontrar a ID de pacote para um aplicativo IOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **ID do lote de aplicativos**: Insira a [ID de lote](bundle-ids-built-in-ios-apps.md) do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Nome do aplicativo**: Insira o nome do aplicativo que você deseja. Você pode mostrar ou ocultar aplicativos internos e aplicativos de linha de negócios. O site da Apple tem uma lista de [aplicativos da Apple internos](https://support.apple.com/HT208094).
- **Editor**: Insira o editor do aplicativo desejado.

Para adicionar aplicações, pode:

- **Adicionar**: Selecione para criar sua lista de aplicativos.
- **Importe** um arquivo CSV com detalhes sobre o aplicativo, incluindo a URL. Utilize o formato `<app url>, <app name>, <app publisher>`. Ou, **Exportar** para criar uma lista de aplicativos restritos que você adicionou, no mesmo formato.

## <a name="wireless"></a>Sem fios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Roaming de dados**: escolha **Bloquear** para impedir o roaming de dados na rede celular. **Não configurado** (predefinição) permite o roaming de dados quando o dispositivo está numa rede móvel.
- **Busca em segundo plano global durante o roaming**: **Bloquear** impede o uso do recurso de busca em segundo plano global ao fazer roaming na rede celular. **Não configurado** (predefinição) permite que o dispositivo obtenha dados, como o e-mail, quando estiver a utilizar o roaming numa rede móvel.
- **Discagem por voz**: escolha **Bloquear** para impedir que os usuários usem o recurso de discagem por voz no dispositivo. **Não configurado** (predefinição) permite a marcação por voz no dispositivo.
- **Roaming de voz**: escolha **Bloquear** para impedir o roaming de voz na rede celular. **Não configurado** (predefinição) permite as chamadas em roaming quando o dispositivo está numa rede móvel.
- **Hotspot pessoal**: o **bloco** desativa o hotspot pessoal no dispositivo dos usuários com cada sincronização de dispositivo. Essa configuração pode não ser compatível com algumas operadoras. **Não configurado** (predefinição) mantém a configuração do hotspot pessoal como o conjunto predefinido pelo utilizador.
- **Regras de uso de celular (somente aplicativos gerenciados)** : define os tipos de dados que os aplicativos gerenciados podem usar quando em redes de celular. As opções são:
  - **Bloquear o uso de dados da rede celular**: bloqueie o uso de dados da rede celular para **todos os aplicativos gerenciados** ou **escolha aplicativos específicos**.
  - **Bloquear o uso de dados da rede celular em roaming**: bloqueie o uso de dados da rede celular quando estiver em roaming para **todos os aplicativos gerenciados** ou **escolha aplicativos específicos**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Alterações nas configurações de uso de dados para celular do aplicativo**: escolha **Bloquear** para evitar alterações nas configurações de uso de dados de celular do aplicativo. **Não configurado** (predefinição) permite que o utilizador controle quais aplicações podem utilizar os dados via rede móvel.
- **Alterações nas configurações do plano celular**: o **bloco** impede que os usuários alterem as configurações no plano da rede celular. **Não configurado** (predefinição) permite que os utilizadores façam alterações.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Modificação do usuário de hotspot pessoal**: quando definido como **Bloquear**, o usuário não pode alterar a configuração de hotspot pessoal. **Não configurado** (padrão) permite que os usuários finais habilitem ou desabilitem seus hotspots pessoais.

  Se você bloquear essa configuração e bloquear a configuração de ponto de interrupção **pessoal** , o hotspot pessoal será desativado.

  Esta funcionalidade aplica-se a:  
  - iOS 12,2 e mais recente

- **Unir redes Wi-Fi usando somente perfis de configuração**: **exigir** força o dispositivo a usar apenas redes Wi-Fi configuradas por meio de perfis de configuração do Intune. **Não configurado** (predefinição) permite que o dispositivo utilize outras redes Wi-Fi.
- **Wi-Fi sempre ativado**: quando definido como **exigir**, o Wi-Fi permanece no aplicativo de configurações. Ele não pode ser desativado em configurações ou no centro de controle, mesmo quando o dispositivo está no modo avião. **Não configurado** (padrão) permite que o usuário controle a ativação ou desativação do Wi-Fi.

  Definir essa configuração não impede que os usuários selecionem uma rede Wi-Fi.

  Esta funcionalidade aplica-se a:  
  - iOS e iPadOS 13,0 e mais recentes

## <a name="connected-devices"></a>Dispositivos Ligados

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Detecção de pulso para Apple Watch emparelhado**: **exigir** força uma Apple Watch emparelhada a usar a detecção de pulso. Quando exigido, o Apple Watch não apresenta notificações quando não estiver a ser utilizado. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Exigir senha de emparelhamento de solicitações de saída do Airplay**: **requer** uma senha de emparelhamento quando o usuário usa o Airplay para transmitir conteúdo para outros dispositivos da Apple. **Não configurado** (predefinição) permite que o utilizador transmita conteúdo através do AirPlay sem introduzir uma palavra-passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- O **essoltar**: **Bloquear** impede o uso do essoltar no dispositivo. **Não configurado** (predefinição) permite utilizar a funcionalidade AirDrop para trocar conteúdo com os dispositivos próximos.
- **Emparelhamento de Apple Watch**: **Bloquear** impede o emparelhamento com um Apple Watch. **Não configurado** (predefinição) permite que o dispositivo seja emparelhado com um Apple Watch.
- **Modificação de Bluetooth**: o **bloco** impede que o usuário final altere as configurações de Bluetooth no dispositivo. **Não configurado** (predefinição) permite que o utilizador altere estas definições.
- **Emparelhamento de host para controlar os dispositivos com os quais um dispositivo IOS pode ser emparelhado**: **não configurado** (padrão) permite o emparelhamento de host para permitir que o administrador controle quais dispositivos um dispositivo IOS pode emparelhar. **Bloquear** impede o emparelhamento de anfitriões.
- **Bloquear o enprint**: escolha o **bloco** para impedir o uso do recurso de impressão no dispositivo. **Não configurado** (predefinição) permite que o utilizador utilize o AirPrint.
  - **Bloquear o armazenamento de credenciais de impressão no**conjunto de chaves: o **bloco** impede o uso do armazenamento de conjunto de chaves para nome de usuário e senha no dispositivo. **Não configurado** (predefinição) permite o armazenamento do nome de utilizador e da palavra-passe do AirPrint na aplicação Keychain.
  - **Exigir um certificado TLS confiável para o esprint**: **exigir** força o dispositivo a usar certificados confiáveis para comunicação de impressão TLS.
  - **Bloquear a descoberta de iBeacon de impressoras de impressão**: **Bloquear** impede que beacons Bluetooth de impressão mal-intencionada de phishing para tráfego de rede. **Não configurado** (predefinição) permite a publicidade de impressoras AirPrint no dispositivo.
- **Bloquear a configuração de novos dispositivos próximos**: o **bloco** desabilita o prompt para configurar novos dispositivos que estão próximos. **Não configurado** (predefinição) permite apresentar avisos aos utilizadores para se ligarem a outros dispositivos Apple próximos.

  Esta funcionalidade aplica-se a:  
  - iOS 11,0 e mais recente

- **Acesso a arquivos na unidade USB**: os dispositivos podem se conectar e abrir arquivos em uma unidade USB. **Desabilitar** impede o acesso do dispositivo à unidade USB no aplicativo arquivos quando um USB está conectado ao dispositivo. Desabilitar esse recurso também impede que os usuários finais transfiram arquivos para uma unidade USB conectada a um iPad. **Não configurado** (padrão) permite o acesso a uma unidade USB no aplicativo arquivos.

  Esta funcionalidade aplica-se a:  
  - iOS e iPadOS 13,0 e mais recentes

## <a name="keyboard-and-dictionary"></a>Teclado e Dicionário

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Pesquisa de definição de palavra**: **Bloquear** impede que o usuário realce uma palavra e, em seguida, procure sua definição no dispositivo. **Não configurado** (predefinição) permite o acesso ao recurso de pesquisa de definição.
- **Teclados de previsão**: **não configurado** (padrão) permite o uso de teclados de previsão para sugerir palavras que o usuário pode querer. **Bloquear** impede esta funcionalidade.
- **Correção automática**: **não configurado** (padrão) permite que o dispositivo corrija automaticamente palavras incorretas. **Bloquear** impede a utilização da correção automática.
- **Verificação ortográfica do teclado**: **não configurado** (padrão) permite o uso do verificador ortográfico no dispositivo. **Bloquear** não permite a verificação ortográfica.
- **Atalhos de teclado**: **não configurado** (padrão) permite o uso de atalhos de teclado no dispositivo. **Bloco** impede o utilizador de utilizar os atalhos de teclado.
- **Dictation**: **Block** impede que o usuário use a entrada de voz para inserir texto. **Não configurado** (predefinição) permite que o utilizador utilize a entrada de ditado.
- **QuickPath**: **não configurado** (padrão) permite que os usuários usem o QuickPath, que permite uma entrada contínua no teclado do dispositivo. Os usuários podem digitar passando o dedo pelas chaves para criar palavras. **Bloquear** impede que os usuários usem o QuickPath. 

  Esta funcionalidade aplica-se a:  
  - iOS 13,0 e iPadOS 13,0 e mais recentes

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

### <a name="settings-apply-to-all-enrollment-types"></a>As configurações se aplicam a: todos os tipos de registro

- **Backup criptografado**: **requer** que os backups de dispositivo sejam criptografados.
- Os **aplicativos gerenciados sincronizam com a nuvem**: **não configurado** (padrão) permite que seus aplicativos de gerenciamento do Intune sincronizem dados com a conta do icloud do usuário. **Bloquear** impede esta sincronização de dados com o iCloud.
- **Bloquear o backup do catálogo corporativo**: escolha **Bloquear** para impedir que os usuários façam backup de livros empresariais. **Não configurado** (padrão) permite que os usuários façam backup desses livros.
- **Bloquear a sincronização de metadados do catálogo corporativo (observações e destaques)** : **Bloquear** impede a sincronização de anotações e destaques em livros empresariais. **Não configurado** (padrão) permite a sincronização.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Sincronização de fluxo de fotos para icloud**: **não configurado** (padrão) permite que os usuários habilitem **meu fluxo de fotos** em seu dispositivo para sincronizar com o iCloud e ter fotos disponíveis em todos os dispositivos do usuário. **Bloquear** impede a sincronização do fluxo de fotografias com o iCloud. O bloqueio desse recurso pode causar perda de dados. 
- **biblioteca de fotos do icloud**: Defina como **Bloquear** para desabilitar usando a biblioteca de fotos do icloud para armazenar fotos e vídeos na nuvem. Todas as fotografias que não tiverem sido completamente transferidas da Fototeca em iCloud para o dispositivo serão removidas do dispositivo. **Não configurado** (padrão) permite usar a biblioteca de fotos do icloud.
- **Fluxo de fotos compartilhado**: escolha o **bloco** para desabilitar o **compartilhamento de fotos do icloud** no dispositivo. **Não configurado** (padrão) permite o streaming de fotos compartilhado.
- **Entrega**: **não configurado** (padrão) permite que os usuários iniciem o trabalho em um dispositivo IOS e, em seguida, continuem o trabalho iniciado em outro dispositivo IOS ou MacOS. **Bloquear** impede esta passagem de informações.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Backup no iCloud**: **não configurado** (padrão) permite que o usuário faça backup do dispositivo no iCloud. **Bloquear** impede que o utilizador faça cópias de segurança do dispositivo para o iCloud.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Bloquear a sincronização de documentos do icloud**: **não configurado** (padrão) permite a sincronização de documento e chave-valor para o espaço de armazenamento do icloud. **Bloquear** impede o iCloud de sincronizar documentos e dados.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

- **Bloquear sincronização**de conjunto de chaves do icloud: escolha o **bloco** para desabilitar a sincronização de credenciais armazenadas no conjunto de chaves no iCloud. **Não configurado** (predefinição) permite aos utilizadores sincronizar estas credenciais.

  A partir do iOS 13,0, essa configuração requer dispositivos supervisionados.

## <a name="autonomous-single-app-mode"></a>Modo de aplicativo único autônomo

Utilize estas definições para configurar os dispositivos iOS para executar aplicações específicas no modo de aplicação única autónomo. Quando este modo está configurado e a aplicação é executada, o dispositivo é bloqueado. Pode executar apenas essa aplicação. Por exemplo, adicione uma aplicação que permita que os utilizadores façam um teste no dispositivo. Quando as ações das aplicações forem concluídas ou quando remover esta política, o dispositivo regressa ao estado de funcionamento normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Nome do aplicativo**: Insira o nome do aplicativo desejado.
- **ID do lote de aplicativos**: Insira a [ID de pacote](bundle-ids-built-in-ios-apps.md) do aplicativo desejado.
- **Adicionar**: Selecione para criar sua lista de aplicativos.

Você também pode **importar** um arquivo CSV com a lista de nomes de aplicativos e suas IDs de pacote. Ou **Exportar** uma lista existente que inclua as aplicações.

## <a name="kiosk"></a>Modo de Local Público

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Aplicativo a ser executado no modo de quiosque**: escolha o tipo de aplicativos que você deseja executar no modo de quiosque. As opções são:
  - **Não configurado** (padrão): as configurações de quiosque não são aplicadas. O dispositivo não é executado no modo de quiosque.
  - **Aplicativo da loja**: Insira a URL para um aplicativo na iTunes App Store.
  - **Aplicativo gerenciado**: escolha um aplicativo que você adicionou ao Intune.
  - **Aplicativo interno**: Insira a ID do [pacote](bundle-ids-built-in-ios-apps.md) do aplicativo interno.

- **Toque assistencial**: **exigir** que a configuração de acessibilidade de toque assistencial esteja no dispositivo. Esta funcionalidade ajuda os utilizadores com os gestos no ecrã que podem ser difíceis para eles. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Inverter cores**: **requer** a configuração de acessibilidade inverter cores para que os usuários com deficiências visuais possam alterar a tela de exibição. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Áudio mono**: **exigir** que a configuração de acessibilidade de áudio mono esteja no dispositivo. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Controle de voz**: **requer** habilitar o controle de voz no dispositivo e permite que os usuários CONTROLEM totalmente o sistema operacional usando comandos Siri. **Não configurado** desabilita o controle de voz no dispositivo.

  Esta definição aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente
  
  > [!TIP]
  > Se você tiver aplicativos LOB disponíveis para sua organização e eles não estiverem no **controle de voz** pronto no dia 0 quando versões Ios 13,0, recomendamos que você deixe essa configuração como **não configurada**.

- **VoiceOver**: **exigir** que a configuração de acessibilidade do VoiceOver esteja no dispositivo para ler o texto na tela em voz alta. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Zoom**: **exigir** que a configuração de zoom esteja no dispositivo para permitir que os usuários usem o toque para ampliar na tela. **Não configurado** não permite executar ou ativar esta funcionalidade no modo de quiosque.
- **Bloqueio automático**: **Bloquear** impede o bloqueio automático do dispositivo. **Não configurado** permite esse recurso.
- **Opção de toque**: **Bloquear** desabilita a opção de toque (mudo) no dispositivo. **Não configurado** permite esse recurso.
- **Rotação de tela**: **Bloquear** impede a alteração da orientação da tela quando o usuário gira o dispositivo. **Não configurado** permite esse recurso.
- **Botão suspensão da tela**: escolha **Bloquear** para desabilitar o botão de ativação de suspensão da tela no dispositivo. **Não configurado** permite esse recurso.
- **Touch**: **Block** desabilita a tela touch no dispositivo. **Não configurado** permite que o utilizador utilize o ecrã tátil.
- **Botões de volume**: **bloco** impede o uso dos botões de volume no dispositivo. **Não configurado** permite os botões de volume.
- **Controle de toque assistencial**: **permitir** que os usuários usem a função de toque assistencial. **Não configurado** desativa esta funcionalidade.
- **Controle inverter cores**: **permitir** alterações de cores invertidas para permitir que os usuários ajustem a função inverter cores. **Não configurado** desativa esta funcionalidade.
- **Falar sobre o texto selecionado**: **permitir que** as configurações de acessibilidade de seleção de fala estejam no dispositivo. Esta funcionalidade lê em voz alta o texto que o utilizador seleciona. **Não configurado** desativa esta funcionalidade.
- **Modificação de controle de voz**: **permite que** os usuários alterem o estado do controle de voz em seus dispositivos. **Não configurado** impede que os usuários alterem o estado do controle de voz em seus dispositivos.

  Esta definição aplica-se a:  
  - iOS 13,0 e mais recente
  - iPadOS 13,0 e mais recente

- **Controle de VoiceOver**: **permitir** alterações de VoiceOver para permitir que os usuários atualizem a função VoiceOver, como o quão rápido o texto na tela é lido em alta. **Não configurado** impede as alterações ao VoiceOver.
- **Controle de zoom**: **permitir** alterações de zoom pelo usuário. **Não configurado** impede as alterações ao zoom.

> [!NOTE]
> Para poder configurar um dispositivo iOS para o modo de local público, tem de utilizar a ferramenta Apple Configurator ou o Programa de Inscrição de Dispositivos Apple para colocar o dispositivo no modo supervisionado. Consulte o guia da Apple sobre a utilização da ferramenta Apple Configurator.
> Se a aplicação iOS que introduziu for instalada após a atribuição do perfil, o dispositivo só entrará em modo de quiosque após ser reiniciado.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo, registro de dispositivo automatizado (supervisionado)

- **Domínios de email desmarcados** > **URL de domínio de email**: Adicione uma ou mais URLs à lista. Quando os utilizadores finais receberem um e-mail de um domínio diferentes dos introduzidos, o e-mail será marcado como não fidedigno na aplicação de E-mail do iOS.

- **Domínios Web geridos** > **URL do Domínio Web**: adicione um ou mais URLs à lista. Quando forem transferidos documentos dos domínios introduzidos, estes serão considerados geridos. Esta definição só se aplica a documentos transferidos através do browser Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>As configurações se aplicam a: registro de dispositivo automatizado (supervisionado)

- **Domínios de preenchimento de senha do Safari** > **URL do domínio**: Adicione uma ou mais URLs à lista. Os utilizadores só podem guardar as palavras-passe Web de URLs nesta lista. Essa configuração se aplica somente ao navegador Safari e dispositivos no modo supervisionado. Se você não inserir nenhuma URL, as senhas poderão ser salvas de todos os sites da Web.

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

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](../device-profile-assign.md) e [monitorize o respetivo estado](../device-profile-monitor.md).

Também pode restringir as funcionalidades e as definições dos dispositivos nos dispositivos [macOS](device-restrictions-macos.md).
