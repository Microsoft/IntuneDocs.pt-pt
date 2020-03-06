---
title: Definições de dispositivos empresariais Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Nos dispositivos Android Enterprise ou Android for Work, restringeas definições no dispositivo, incluindo cópia e pasta, notificações de exibição, permissões de aplicações, partilha de dados, comprimento da palavra-passe, registo de falhas, utilização de impressões digitais para desbloquear, reutilizar palavras-passe e ativar bluetooth partilha de contactos de trabalho. Configure os dispositivos como um quiosque dedicado para executar uma aplicação, ou várias aplicações.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122f0b0194a96b844e274ab39a73224eb23cc6b3
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368983"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos do Android Enterprise para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de gestão de dispositivos móveis (MDM), utilize estas definições para permitir ou desativar funcionalidades, executar aplicações em dispositivos dedicados, segurança de controlo e muito mais.

## <a name="before-you-begin"></a>Antes de começar

Criar um perfil de [configuração do dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

Estas definições aplicam-se aos tipos de inscrição do Android Enterprise onde o Intune controla todo o dispositivo, como dispositivos Android Enterprise Totalmente Geridos ou Dedicados.

### <a name="general-settings"></a>Definições gerais

- **Captura do** **ecrã** : Escolha o Bloco para evitar imagens ou capturas de ecrã no dispositivo. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Câmara**: Escolha **o Bloco** para impedir o acesso à câmara no dispositivo. **Não é necessário** que o acesso à câmara do dispositivo.
- **Política de permissões predefinida**: esta definição configura a política de permissões predefinida para pedidos de permissões de runtime. Os valores possíveis incluem:
  - **Predefinição do dispositivo**: utiliza a predefinição do dispositivo.
  - **Pedir**: é pedido ao utilizador que aprove a permissão.
  - **Conceder automaticamente**: as permissões são concedidas automaticamente.
  - **Negar automaticamente**: as permissões são negadas automaticamente.
- **Alterações de data e hora**: Escolha o **Bloco** para evitar que os utilizadores definam manualmente a data e a hora. **Não configurado** permite aos utilizadores a data e hora definidas no dispositivo.
- **Alterações de volume**: **O bloco** impede que os utilizadores mudem o volume do dispositivo e também silencia o volume principal. **Não configurado** permite utilizar as definições de volume no dispositivo.
- **Reset de fábrica**: Escolha o **Bloco** para evitar que os utilizadores utilizem a opção de reset de fábrica nas definições do dispositivo. **Não configurado** permite que os utilizadores utilizem esta definição no dispositivo.
- **Arranque seguro**: selecione **Bloquear** para impedir que os utilizadores reiniciem o dispositivo em modo de segurança. **Não configurado** permite que os utilizadores reiniciem o dispositivo em modo de segurança.
- **Barra de estado**: Escolha **o Bloco** para impedir o acesso à barra de estado, incluindo notificações e configurações rápidas. **Não configurado** permite aos utilizadores o acesso à barra de estado.
- **Serviços**de dados de roaming : Escolha **o Bloco** para evitar que os dados circulam pela rede celular. **Não configurado** permite o roaming de dados quando o dispositivo está numa rede celular.
- **Alterações de definição de Wi-Fi**: Escolha o **Bloco** para evitar que os utilizadores mudem as definições de Wi-Fi criadas pelo proprietário do dispositivo. Os utilizadores podem criar suas próprias configurações de Wi-Fi. **Não configurado** permite que os utilizadores alterem as definições de Wi-Fi no dispositivo.
- **Configuração do ponto de acesso Wi-Fi**: Escolha o **Bloco** para evitar que os utilizadores criem ou mudem quaisquer configurações wi-fi. **Não configurado** permite que os utilizadores alterem as definições de Wi-Fi no dispositivo.
- **Configuração Bluetooth**: Escolha **o Bloco** para evitar que os utilizadores configurem Bluetooth no dispositivo. **Não configurado** permite utilizar Bluetooth no dispositivo.
- **Amarração e acesso a hotspots**: Escolha **o Bloco** para evitar a amarração e o acesso a hotspots portáteis. **Não configurado** permite a amarração e o acesso a hotspots portáteis.
- **Armazenamento USB**: Escolha **permitir** aceder ao armazenamento USB no dispositivo. **Não configurado** impede o acesso ao armazenamento USB.
- **Transferência de ficheiros USB**: Escolha **o Bloco** para evitar a transferência de ficheiros para USB. **Não configurado** permite a transferência de ficheiros.
- **Meios externos**: Escolha **o Bloco** para evitar a utilização ou ligação de qualquer meio externo no dispositivo. **Não configurado** permite meios externos no dispositivo.
- Dados de **feixes utilizando NFC**: Escolha **o Bloco** para evitar a utilização da tecnologia Near Field Communication (NFC) para obter dados de aplicações. **Não configurado** permite a utilização do NFC para partilhar dados entre dispositivos.
- **Funcionalidades de depuração**: Escolha **permitir** que os utilizadores utilizem funcionalidades de depuração no dispositivo. **Não configurado** impede que os utilizadores utilizem as funcionalidades de depuração no dispositivo.
- **Regulação do microfone**: Escolha o **bloco** para evitar que os utilizadores desloquem o microfone e ajustem o volume do microfone. **O utilizador não configurado** permite que o utilizador utilize e ajuste o volume do microfone no dispositivo.
- **E-mails**de proteção de reset de fábrica : Escolha endereços de **e-mail da conta google**. Introduza os endereços de e-mail dos administradores de dispositivos que possam desbloquear o dispositivo depois de serem eliminado. Certifique-se de separar os endereços de e-mail com um ponto e vírgula, como `admin1@gmail.com;admin2@gmail.com`. Se uma mensagem de e-mail não é inserida, qualquer pessoa pode desbloquear o dispositivo após o restauro para as definições de fábrica. Estes e-mails só se aplicam quando uma fábrica não utilizadora é reaberta, como executar uma reposição de fábrica usando o menu de recuperação.
- **Saída de rede :** Escolha **ativar** para permitir que os utilizadores liguem a função de saída da rede. Se uma conexão de rede não é feita quando o dispositivo for arrancado, a saída de emergência pede para temporariamente ligar a uma rede e atualizar a política de dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Esta funcionalidade liga dispositivos a uma rede se:
  - Não existe uma rede adequada na política de última.
  - O dispositivo for arrancado numa aplicação no modo de bloqueio de tarefa.
  - O utilizador é não é possível alcançar as definições do dispositivo.

  **Não configurado** impede que os utilizadores ligassem a função de saída da rede no dispositivo.

- **Atualização do sistema**: Escolha uma opção para definir como o dispositivo lida com atualizações over-the-air:
  - **Predefinição do Dispositivo**: utiliza a predefinição do dispositivo.
  - **Automático**: as atualizações são instaladas automaticamente sem interação do utilizador. Definir esta política imediatamente instala todas as atualizações pendentes.
  - **Adiado**: as atualizações são adiadas por 30 dias. No final dos 30 dias, o Android solicita ao utilizador para instalar a atualização. É possível os fabricantes de dispositivos ou operadoras impedirem (isentarem) o adiamento de atualizações de segurança importantes. Uma atualização isenta mostra uma notificação de sistema ao utilizador no dispositivo.
  - **Janela de manutenção**: as atualizações são instaladas automaticamente durante uma janela de manutenção diária definida no Intune. Instalação tenta diariamente durante 30 dias e pode falhar se houver níveis insuficientes de espaço ou útil da bateria. Após 30 dias, o Android solicita ao utilizador que instalar. Esta janela também é utilizada para instalar atualizações para aplicações do Play. Utilize esta opção para dispositivos dedicados, como quiosques, uma vez que as aplicações de primeiro plano dedicadas a dispositivos únicos podem ser atualizadas.

- **Janelas de notificação**: Quando definido para **Desativar,** notificações de janelas, incluindo torradas, chamadas recebidas, chamadas de saída, alertas de sistema e erros do sistema não são mostrados no dispositivo. Quando definido para **Não configurado,** o predefinido do sistema operativo é utilizado, o que pode ser para mostrar notificações.
- **Ignore as dicas de utilização inicial**: **Ative** ocultar ou ignora sugestões de apps que passem por tutoriais ou sugestões quando a aplicação começa. Quando definido para **Não configurado,** o predefinido do sistema operativo é utilizado, o que pode mostrar estas sugestões quando a aplicação começa.

### <a name="system-security-settings"></a>Definições de segurança do sistema

- **A varredura de ameaças em apps**: **Require** (padrão) permite ao Google Play Protect digitalizar aplicações antes e depois de serem instaladas. Se detetar uma ameaça, poderá alertar o utilizador para remover a aplicação do dispositivo. **Não configurado** não permite ou executa o Google Play Protect para digitalizar aplicações.

### <a name="dedicated-device-settings"></a>Definições dedicadas do dispositivo

Utilize estas definições para configurar uma experiência de estilo quiosque nos seus dispositivos dedicados. Pode configurar um dispositivo para executar uma aplicação ou executar muitas aplicações. Quando um dispositivo é definido com o modo de quiosque, apenas as aplicações que adiciona estão disponíveis. Estas definições aplicam-se a dispositivos dedicados ao Android Enterprise. Não se aplicam a dispositivos geridos pela Android Enterprise.

**Modo quiosque**: Escolha se o dispositivo executa uma aplicação ou executa várias aplicações.

- **Aplicação única**: Os utilizadores só podem aceder a uma única aplicação no dispositivo. Quando o dispositivo é iniciado, apenas a aplicação específica é iniciada. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

  - **Selecione uma aplicação gerida**: Selecione a aplicação gerida do Google Play na lista.

    Se não tiver nenhuma aplicação listada, [adicione algumas aplicações Android](../apps/apps-add-android-for-work.md) ao dispositivo. Certifique-se de [atribuir a app ao grupo de dispositivos criado para os seus dispositivos dedicados](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Ao utilizar o modo de quiosque de aplicações únicas, as aplicações dialerador/telefone podem não funcionar corretamente. 
  
- **Multi-aplicações:** Os utilizadores podem aceder a um conjunto limitado de aplicações no dispositivo. Quando o dispositivo é iniciado, inicie apenas as aplicações que adicionar. Também pode adicionar alguns links da web que os utilizadores podem abrir. Quando a política é aplicada, os utilizadores veem ícones para aplicações permitidas na tela inicial.

  > [!IMPORTANT]
  > Para dispositivos dedicados a várias aplicações, a [aplicação Managed Home Screen](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) do Google Play **deve ser:**
  >   - [Adicionado como uma aplicação de cliente](../apps/apps-add-android-for-work.md) em Intune
  >   - [Atribuído ao grupo de dispositivos](../apps/apps-deploy.md) criado para os seus dispositivos dedicados
  >
  > A aplicação **Managed Home Screen** não é necessária para estar no perfil de configuração, mas é necessário ser adicionada como uma aplicação de cliente. Quando a aplicação **Managed Home Screen** é adicionada como uma aplicação para clientes, quaisquer outras aplicações que adicione no perfil de configuração são mostradas como ícones na aplicação **Managed Home Screen.**
  >
  > Ao utilizar o modo de quiosque multi-aplicações, as aplicações de dialer/telefone podem não funcionar corretamente. 

  - **Adicione:** Selecione as suas aplicações da lista.

    Se a aplicação **Managed Home Screen** não estiver listada, [adicione-a a partir do Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Certifique-se de [atribuir a app](../apps/apps-deploy.md) ao grupo de dispositivos criado para os seus dispositivos dedicados.

    Também pode adicionar [outras aplicações Android](../apps/apps-add-android-for-work.md) e [aplicações web](../apps/web-app.md) criadas pela sua organização ao dispositivo. Certifique-se de [atribuir a app ao grupo de dispositivos criado para os seus dispositivos dedicados](../apps/apps-deploy.md).

  - **Botão doméstico virtual**: Um botão soft-key que devolve os utilizadores ao Ecrã Home Gerido para que os utilizadores possam alternar entre apps. As opções são:

    - **Não configurado** (predefinido): Não é mostrado um botão inicial. Os utilizadores devem usar o botão traseiro para alternar entre aplicações.
    - **Swipe up**: Um botão doméstico mostra quando um utilizador passa para cima no dispositivo.
    - **Flutuação**: Mostra um botão doméstico persistente e flutuante no dispositivo.

  - **Modo de quiosque :** Escolha **ativar** para permitir que os administradores interrompam temporariamente o modo de quiosque para atualizar o dispositivo. Para utilizar esta funcionalidade, o administrador:
  
    1. Continua a selecionar o botão traseiro até que seja mostrado o botão do **quiosque de saída.** 
    2. Seleciona o botão **de quiosque de saída** e introduz o código pin do modo de quiosque **Leave.**
    3. Quando terminar, selecione a aplicação **Managed Home Screen.** Este passo relocks o dispositivo em modo de local público de várias aplicações.

      Quando definido para **Não configurado,** os administradores não podem parar o modo de quiosque. Se o administrador continuar a selecionar o botão de trás e selecionar o botão de **quiosque de saída,** então uma mensagem indica que é necessária uma senha.

    - **Deixe**o código do modo quiosque : Introduza um PIN numérico de 4-6 dígitos. O administrador utiliza este PIN para interromper temporariamente o modo de local público.

  - **Definir o fundo de URL personalizado**: Introduza um URL para personalizar o ecrã de fundo no dispositivo dedicado.

    > [!NOTE]
    > Para a maioria dos casos, recomendamos começar com imagens de pelo menos os seguintes tamanhos:
    >
    > - Telefone: 1080x1920 px
    > - Tablet: 1920x1080 px
    >
    > Para a melhor experiência e detalhes nítidos, sugere-se que os ativos de imagem por dispositivo sejam criados de acordo com as especificações de exibição.
    >
    > Os ecrãs modernos têm densidades de pixels mais elevadas e podem exibir imagens de definição equivalentes de 2K/4K.

  - **Configuração Wi-Fi**: **Ativar** mostra o controlo Wi-Fi no Ecrã Home Gerido e permite que os utilizadores finais conectem o dispositivo a diferentes redes Wi-Fi. Ativar esta funcionalidade também liga a localização do dispositivo. **Não configurado** (predefinido) não mostra o controlo Wi-Fi no Ecrã Home Gerido. Impede que os utilizadores se conectem às redes Wi-Fi enquanto utilizam o Ecrã Home Gerido.

  - **Configuração Bluetooth**: **Ativar** mostra o controlo Bluetooth no Ecrã Home Gerido e permite que os utilizadores finais emparelhem dispositivos em vez de Bluetooth. Ativar esta funcionalidade também liga a localização do dispositivo. **Não configurado** (predefinido) não mostra o controlo Bluetooth no Ecrã Inicial Gerido. Impede os utilizadores de configurar em dispositivos Bluetooth e emparelhamento durante a utilização do Ecrã Home Gerido.

  - **Acesso à lanterna**: **Ativar** mostra o controlo da lanterna no Ecrã Home Gerido e permite que os utilizadores finais liguem ou desliguem a lanterna. **Não configurado** (predefinido) não mostra o controlo da lanterna no Ecrã Home Gerido. Impede que os utilizadores utilizem a lanterna durante a utilização do Ecrã Home Gerido.

  - **Controlo de volume**de mídia : **Ativar** mostra o controlo de volume de mídia no Ecrã Home Gerido e permite que os utilizadores finais ajustem o volume de suporte do dispositivo utilizando um slider. **Não configurado** (predefinido) não mostra o controlo de volume de mídia no Ecrã Home Gerido. Impede que os utilizadores ajustem o volume de suporte do dispositivo enquanto utilizam o Ecrã Home Gerido, a menos que os seus botões de hardware o suportem. 

  - **Modo**de poupança de ecrã : **Ativar** mostra um protetor de ecrã no Ecrã Home Gerido quando o dispositivo está bloqueado ou que está fora. **Não configurado** (predefinido) não mostra um protetor de ecrã no Ecrã Principal Gerido.

    Quando ativado, configure também:

    - **Definir imagem de poupança**de ecrã personalizada : Introduza o URL num PNG personalizado, JPG, JPEG, GIF, BMP, WebP ou ICOimage. Por exemplo, introduza:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      Se não introduzir um URL, então a imagem padrão do dispositivo é utilizada, se houver uma imagem predefinida.
      
      > [!TIP]
      > Qualquer URL de recurso de ficheiro que possa ser transformado num bitmap é suportado.

    - **Número de segundos o dispositivo mostra o protetor de ecrã antes**de desligar o ecrã : Escolha quanto tempo o dispositivo mostra o protetor de ecrã. Introduza um valor entre 0-9999999 segundos. O padrão é `0` segundos. Quando deixada em branco, ou definida a zero (`0`), o protetor de ecrã está ativo até que um utilizador interaja com o dispositivo.
    - **Número de segundos em**que o dispositivo está inativo antes de mostrar o protetor de ecrã : Escolha o tempo que o dispositivo está inativo antes de mostrar o protetor de ecrã. Introduza um valor entre 1-9999999 segundos. O padrão é `30` segundos. Deve introduzir um número superior a zero (`0`).
    - **Detete os meios de comunicação antes**de iniciar o protetor de ecrã : **Ativar** (predefinido) não mostra o protetor de ecrã se o áudio ou o vídeo estiverem a reproduzir-se no dispositivo. **Não configurado** mostra o protetor de ecrã, mesmo que o áudio ou o vídeo esteja a ser reproduzido.

### <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Desativar o ecrã**de bloqueio : Escolha **desativar** para evitar que os utilizadores utilizem a função de bloqueio do Keyguard no dispositivo. **Não configurado** permite ao utilizador utilizar as funcionalidades Keyguard.
- **Características do ecrã de bloqueio desativado**: Quando o teclado estiver ativado no dispositivo, escolha quais as funcionalidades a desativar. Por exemplo, quando a **câmara Segura** é verificada, a função da câmara é desativada no dispositivo. Quaisquer funcionalidades não verificadas estão ativadas no dispositivo.

  Estas funcionalidades estão disponíveis para os utilizadores quando o dispositivo está bloqueado. Os utilizadores não verão ou acederão a funcionalidades que sejam verificadas.

- **Tipo de palavra-passe necessária**: define o tipo de palavra-passe necessária para o dispositivo. As opções são:
  - **Predefinição do dispositivo**
  - **Palavra-passe obrigatória, sem restrições**
  - **Biométrico fraco**: [Biometria forte vs. biométrico fraco](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre o site do Android)
  - **Numérico:** A palavra-passe só deve ser números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Complexo numérico**: Números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfabética:** São necessárias letras no alfabeto. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico:** Inclui letras maiúsculas, letras minúsculas e caracteres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico com símbolos**: Inclui letras maiúsculas, letras minúsculas, caracteres numéricos, marcas de pontuação e símbolos. Introduza também:

    - Comprimento mínimo da **palavra-passe**: Introduza o comprimento mínimo que a palavra-passe deve ter, entre 4 e 16 caracteres.
    - **Número de caracteres necessários**: Introduza o número de caracteres que a palavra-passe deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres minúsculos necessários**: Introduza o número de caracteres minúsculos que a palavra-passe deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres maiúsculos necessários**: Introduza o número de caracteres maiúsculos que a palavra-passe deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres não-letra necessários**: Introduza o número de não-letras (qualquer outra coisa que não seja letras no alfabeto) a palavra-passe deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres numéricos necessários**: Introduza o número de caracteres numéricos (`1`, `2`, `3`, e assim por diante) a palavra-passe deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres de símbolo necessários**: Introduza o número de caracteres de símbolos (`&`, `#`, `%`, e assim por diante) a palavra-passe deve ter, entre 0 e 16 caracteres.

- Número de dias até que a **palavra-passe expire**: Introduza o número de dias, entre 1-365, até que a palavra-passe do dispositivo seja alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.
- **Número de palavras-passe necessárias antes de o utilizador poder reutilizar uma palavra-passe**: Introduza o número de senhas recentes que não podem ser reutilizadas, entre 1 e 24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.
- **Número de falhas de entrada antes de limpar o dispositivo**: Introduza o número, entre 4 e 11, de inscrições falhadas para permitir antes de o dispositivo ser limpo.

### <a name="power-settings"></a>Definições de energia

- **Tempo para bloquear o ecrã**: Introduza o tempo máximo que um utilizador pode definir até que o dispositivo bloqueie. Por exemplo, se ajustar esta definição para **10 minutos,** então os utilizadores podem definir o tempo de 15 segundos até 10 minutos. Quando definido para **Não configurado** (predefinido), Intune não altera nem controla esta definição.

- **Ecrã ligado enquanto o dispositivo está ligado**: selecione que fontes de energia fazem com que o ecrã do dispositivo permaneça ligado enquanto o dispositivo está ligado.

### <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos utilizadores**: selecione **Bloquear** para impedir que os utilizadores adicionem novos utilizadores. Cada utilizador tem um espaço pessoal no dispositivo para personalizado Home ecrãs, contas, aplicações e definições. **Não configurado** (predefinido) permite que os utilizadores adicionem outros utilizadores ao dispositivo.
- **Remoção do utilizador**: selecione **Bloquear** para impedir que os utilizadores removam utilizadores. **Não configurado** (predefinido) permite que os utilizadores removam outros utilizadores do dispositivo.
- **Alterações na conta** (apenas dispositivos dedicados): Escolha **o Bloco** para evitar que os utilizadores modifiquem as contas. **Não configurado** (predefinido) permite que os utilizadores atualizem as contas do utilizador no dispositivo.

  > [!NOTE]
  > Esta definição não é honrada em dispositivos proprietários de dispositivos (totalmente geridos). Se configurar esta definição, a definição é ignorada e não tem impacto.

- **O utilizador pode configurar credenciais**: **O Bloco** impede os utilizadores de configurar em dispositivos os certificados, mesmo dispositivos que não estejam associados a uma conta de utilizador. **Não configurado** pode permitir que os utilizadores configurem ou alterem as suas credenciais quando acedem às mesmas na loja de chaves. 
- **Contas pessoais**do Google : **O Bloco** impede os utilizadores de adicionarem a sua conta pessoal da Google ao dispositivo. **Não configurado** (predefinido) permite que os utilizadores adicionem a sua conta pessoal do Google.

### <a name="applications"></a>Aplicações

- **Permitir a instalação a partir de fontes desconhecidas**: Escolha **permitir** para que os utilizadores possam ligar **fontes desconhecidas**. Esta definição permite que as aplicações se instalem a partir de fontes desconhecidas, incluindo outras fontes que não a Google Play Store. **Não configurado** impede que os utilizadores acendam **fontes desconhecidas.**
- **Permitir o acesso a todas as aplicações na loja Google Play**: Quando definido para **permitir,** os utilizadores têm acesso a todas as aplicações na loja Google Play. Não têm acesso às aplicações que o administrador bloqueia nas [Aplicações de Clientes.](../apps/apps-add-android-for-work.md) **Não configurado** obriga os utilizadores a aceder apenas às aplicações que o administrador disponibiliza a Google Play Store, ou aplicações necessárias nas [Aplicações do Cliente.](../apps/apps-add-android-for-work.md)
- **Atualizações automáticas**da aplicação : Escolha quando as atualizações automáticas forem instaladas. As opções são:
  - **Não configurado**
  - **Escolha do utilizador**
  - **Nunca**
  - **Apenas Wi-Fi**
  - **Sempre**

### <a name="connectivity"></a>Conectividade

- **VPN always-on**: selecione **Ativar** para definir um cliente VPN para se ligar e voltar a ligar à VPN automaticamente. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN sempre on para um único dispositivo. A implementação de múltiplas políticas de VPN sempre on para um único dispositivo não é suportada.

- **Cliente VPN**: selecione um cliente VPN que suporte a funcionalidade Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID de Pacote**: introduza o ID do pacote da aplicação na Google Play Store. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  > - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  > - Ainda precisa de configurar o cliente VPN com um [perfil VPN](vpn-settings-android-enterprise.md), ou através de um perfil de configuração de [aplicações](../apps/app-configuration-policies-use-android.md).
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Consulte [as notas de lançamento do F5 para o Acesso F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolha **ativar** para forçar todo o tráfego de rede a utilizar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

- **Proxy global recomendado**: Escolha **ativar** para adicionar um proxy global aos dispositivos. Quando ativado, o tráfego HTTP e HTTPS, incluindo algumas aplicações no dispositivo, utilize o proxy em que entra. Este representante é apenas uma recomendação. É possível que algumas aplicações não usem o proxy. **Não configurado** (padrão) não adiciona um proxy global recomendado.

  Para obter mais informações sobre esta funcionalidade, consulte [o setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (abre um site Android).

  Quando ativado, introduza também o **tipo** de procuração. As opções são:

  - **Direto**: Escolha esta opção para introduzir manualmente os dados do servidor proxy, incluindo:
    - **Anfitrião**: Introduza o nome de anfitrião ou endereço IP do seu servidor proxy. Por exemplo, introduza: `proxy.contoso.com` ou `127.0.0.1`.
    - **Número**da porta : Introduza o número da porta TCP utilizado pelo servidor proxy. Por exemplo, introduza `8080`.
    - **Anfitriões excluídos**: Introduza uma lista de nomes de anfitriões ou endereços IP que não utilizem o proxy. Esta lista pode incluir um wildcard asterisco (`*`) e vários anfitriões separados por pontos evímetros (`;`) sem espaços. Por exemplo, introduza `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - **Proxy Auto-Config**: Introduza o **URL PAC** num script de configuração automática proxy. Por exemplo, introduza `https://proxy.contoso.com/proxy.pac`.

    Para obter mais informações sobre ficheiros PAC, consulte o [ficheiro Proxy Auto-Configuration (PAC)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (abre um site não Microsoft).

## <a name="work-profile-only"></a>Apenas perfil de trabalho

Estas definições aplicam-se aos tipos de inscrição do Android Enterprise onde o Intune controla apenas o Perfil de Trabalho, como a inscrição do perfil android Enterprise Work num dispositivo pessoal ou de trazer o seu próprio dispositivo (BYOD).

### <a name="work-profile-settings"></a>Definições de perfil de trabalho

#### <a name="general"></a>Geral

- **Copiar e colar entre trabalho e perfis pessoais**: Escolha **o Bloco** para evitar a cópia e a pasta entre o trabalho e as aplicações pessoais. **Não configurado** permite que os utilizadores partilhem dados usando cópia e pasta com aplicações no perfil pessoal 
- **Partilha de dados entre trabalho e perfis pessoais**: Escolha se as aplicações no perfil de trabalho podem partilhar com aplicações no perfil pessoal. Por exemplo, pode controlar ações de partilha dentro de aplicações, como a **Partilha...** na aplicação do browser Chrome. Esta definição não se aplica ao comportamento da área de transferência de copiar/colar. As opções de partilha:
  - **Padrão do dispositivo**: O comportamento de partilha padrão do dispositivo, que varia consoante a versão Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. Em dispositivos com a versão 6.0 e versões posteriores, a Google não bloqueia a partilha do perfil pessoal para o perfil de trabalho.
  - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal**: ativa a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Evite qualquer partilha além-fronteiras**: Impede a partilha entre trabalho e perfis pessoais.
  - **Sem restrições à partilha**: Permite a partilha através do limite do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Esta definição permite que aplicações geridas no perfil de trabalho partilhem com aplicações no lado não gerido do dispositivo. Por isso, utilize esta definição com cuidado.

- **Notificações**de perfil de trabalho enquanto o dispositivo está bloqueado : Controla se as aplicações no perfil de trabalho podem apresentar dados em notificações quando o dispositivo está bloqueado. **O Bloco** não mostra os dados. **Não configurado** mostra os dados.
- **Permissões de aplicações predefinidas**: define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Utilize esta política para conceder permissões automaticamente sem aviso, recusar permissões automaticamente sem aviso ou permitir que o utilizador final decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

  Também pode utilizar uma política de Configuração de Aplicações para conceder permissões a aplicações individuais (**Aplicações Cliente** > **Políticas de configuração da aplicação**).

- **Adicionar e remover contas**: Escolha **o Bloco** para evitar que os utilizadores finais adicionem ou removam manualmente as contas no perfil de trabalho. Por exemplo, ao implementar a aplicação Gmail num perfil de trabalho do Android, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho. **Não configurado** permite adicionar contas no perfil de trabalho.  

  > [!NOTE]
  > As contas do Google não podem ser adicionadas a um perfil de trabalho.

- **Partilha de contactos por Bluetooth**: permite aceder aos contactos do trabalho a partir de outro dispositivo, como um automóvel, que esteja emparelhado através de Bluetooth. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Ativar esta definição pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura do** **ecrã** : Escolha o Bloco para evitar imagens ou capturas de ecrã no dispositivo no perfil de trabalho. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite obter imagens.

- **Mostrar**o contacto do trabalho no perfil pessoal : Quando**ativado (Não configurado),** os dados do contacto de trabalho são apresentados no perfil pessoal. Quando definido para **bloquear,** o número de contato de trabalho não é apresentado no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Pesquisar contactos de trabalho a partir de perfil pessoal**: Escolha o **Bloco** para impedir que os utilizadores procurem contactos de trabalho em aplicações no perfil pessoal. **Não é necessário** que permita procurar contactos de trabalho no perfil pessoal.

- **Câmara**: Escolha **o Bloco** para impedir o acesso à câmara no dispositivo no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição. **Não é necessário** que o acesso à câmara no perfil de trabalho.

- **Permitir widgets a partir de aplicações de perfil de trabalho**: **Enable** permite que os utilizadores finais coloquem widgets expostos por aplicações no ecrã principal. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

  Por exemplo, o Outlook está instalado nos perfis de trabalho dos seus utilizadores. Quando definido para **Ativar,** os utilizadores podem colocar o widget da agenda no ecrã principal do dispositivo.

#### <a name="work-profile-password"></a>Palavra-passe de perfil de trabalho

- **Exigir Palavra-passe de Perfil de Trabalho**: aplica-se ao Android 7.0 e posterior com o perfil de trabalho ativado. Escolha **Exigir** introduzir uma política de código de acesso que se aplique apenas às aplicações no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois. **Não configurado** permite ao utilizador utilizar aplicações de trabalho, sem introduzir uma palavra-passe.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter, de **4**-**16**.
- **Máximo de minutos de inatividade até ao bloqueio do perfil de trabalho**: selecione a quantidade de tempo antes de o perfil de trabalho ser bloqueado. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de o perfil de trabalho do dispositivo ser eliminado.
- **Expiração da palavra-passe (dias)** : introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
- **Tipo de palavra-passe necessária**: selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio de impressões digitais**: Escolha o **Bloco** para evitar que os utilizadores finais utilizem o scanner de impressões digitais do dispositivo para desbloquear o dispositivo. **Não configurado** permite que os utilizadores desbloqueiem dispositivos com uma impressão digital no perfil de trabalho.
- **Smart Lock e outros agentes fidedignos**: Escolha o **Bloco** para evitar que o Smart Lock ou outros agentes fidedignos ajustem as definições do ecrã de bloqueio em dispositivos compatíveis. Esta funcionalidade, também conhecida como agente fiduciário, permite-lhe desativar ou contornar a palavra-passe do ecrã de bloqueio do dispositivo se o dispositivo estiver num local de confiança. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="device-password"></a>Palavra-passe do dispositivo

Estas definições de palavra-passe aplicam-se aos perfis pessoais nos dispositivos que utilizam um perfil de trabalho.

- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter, de **4**-**14**.
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de o perfil de trabalho do dispositivo ser eliminado.
- **Expiração da palavra-passe (dias)** : introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**)
- **Tipo de palavra-passe necessária**: selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: introduza o número de novas palavras-passe que têm de ser utilizadas antes de poder ser reutilizada uma antiga (**1**-**24**).
- **Desbloqueio de impressões digitais**: Escolha **o Bloco** para evitar que o utilizador final utilize o scanner de impressões digitais do dispositivo para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes fidedignos**: Escolha o **Bloco** para evitar que o Smart Lock ou outros agentes fidedignos ajustem as definições do ecrã de bloqueio em dispositivos compatíveis. Esta funcionalidade, também conhecida como agente fiduciário, permite-lhe desativar ou contornar a palavra-passe do ecrã de bloqueio do dispositivo se o dispositivo estiver num local de confiança. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="system-security"></a>Segurança do sistema

- **Verificação de ameaças em apps**: **Exigir** aplicações que a definição de Apps **de Verificação** está ativada para trabalho e perfis pessoais.

   > [!Note]
   > Esta definição funciona apenas para dispositivos que são Android 8 (Oreo) e acima.

- **Evite instalações de aplicações de fontes desconhecidas no perfil pessoal**: Por design, os dispositivos de perfil de trabalho android Enterprise não podem instalar aplicações de outras fontes que não a Play Store. Por natureza, os dispositivos de perfil de trabalho destinam-se a ter duplo perfil:

  - Um perfil de trabalho gerido usando MDM.
  - Um perfil pessoal isolado da gestão do MDM.

  Esta definição permite aos administradores um maior controlo das instalações de aplicações de fontes desconhecidas. **Não configurado** (predefinido) permite instalações de aplicações de fontes desconhecidas no perfil pessoal. **O bloco** impede instalações de aplicações de outras fontes que não a Play Store no perfil pessoal.

### <a name="connectivity"></a>Conectividade

- **VPN always-on**: selecione **Ativar** para definir um cliente VPN para se ligar e voltar a ligar à VPN automaticamente. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN Sempre Ativada num único dispositivo. Não é suportado implementar várias políticas de VPN Sempre Ativada num único dispositivo.

- **Cliente VPN**: selecione um cliente VPN que suporte a funcionalidade Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID de Pacote**: introduza o ID do pacote da aplicação na Google Play Store. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  > - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Consulte [as notas de lançamento do F5 para o Acesso F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolha **ativar** para forçar todo o tráfego de rede a utilizar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de quiosque de dispositivos dedicados para dispositivos [Android](device-restrictions-android.md#kiosk) e [Windows 10.](kiosk-settings.md)

## <a name="see-also"></a>Veja também

[Configurar e resolver problemas dispositivos empresariais Android no Microsoft Intune](https://support.microsoft.com/help/4476974)
