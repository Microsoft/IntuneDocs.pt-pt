---
title: Configurações de dispositivo do Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos Android Enterprise ou Android for Work, restrinja as configurações no dispositivo, incluindo copiar e colar, Mostrar notificações, permissões de aplicativo, compartilhamento de dados, comprimento da senha, falhas de entrada, usar impressão digital para desbloquear, reutilizar senhas e habilitar Bluetooth compartilhamento de contatos de trabalho. Configure dispositivos como um quiosque de dispositivo dedicado para executar um aplicativo ou vários aplicativos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29c5fc03285535565a4db57ea013f72a2936439
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72494054"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Configurações de dispositivo do Android Enterprise para permitir ou restringir recursos usando o Intune

Este artigo lista e descreve as diferentes configurações que você pode controlar em dispositivos Android Enterprise. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, executar aplicativos em dispositivos dedicados, controlar a segurança e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Somente proprietário do dispositivo

### <a name="general-settings"></a>Definições gerais

- **Captura de tela**: escolha **Bloquear** para impedir capturas de tela ou capturas de telas no dispositivo. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite que o usuário Capture o conteúdo da tela como uma imagem.
- **Câmera**: escolha **Bloquear** para impedir o acesso à câmera no dispositivo. **Não obrigatório** permite o acesso à câmera do dispositivo.
- **Política de permissões predefinida**: esta definição configura a política de permissões predefinida para pedidos de permissões de runtime. Os valores possíveis incluem:
  - **Predefinição do dispositivo**: utiliza a predefinição do dispositivo.
  - **Pedir**: é pedido ao utilizador que aprove a permissão.
  - **Conceder automaticamente**: as permissões são concedidas automaticamente.
  - **Negar automaticamente**: as permissões são negadas automaticamente.
- **Alterações de data e hora**: escolha **Bloquear** para impedir que os usuários configurem manualmente a data e a hora. **Não configurado** permite que os usuários definam a data e a hora do dispositivo.
- **Alterações de volume**: selecione **Bloquear** para impedir que os utilizadores alterem o volume do dispositivo. **Não configurado** permite usar as configurações de volume no dispositivo.
- **Redefinição de fábrica**: escolha **Bloquear** para impedir que os usuários usem a opção de redefinição de fábrica nas configurações do dispositivo. **Não configurado** permite que os usuários usem essa configuração no dispositivo.
- **Arranque seguro**: selecione **Bloquear** para impedir que os utilizadores reiniciem o dispositivo em modo de segurança. **Não configurado** permite que os usuários reiniciem o dispositivo no modo de segurança.
- **Barra de status**: escolha **Bloquear** para impedir o acesso à barra de status, incluindo notificações e configurações rápidas. **Não configurado** permite que os usuários acessem a barra de status.
- **Serviços de dados de roaming**: escolha **Bloquear** para impedir o roaming de dados na rede celular. **Não configurado** permite o roaming de dados quando o dispositivo está em uma rede de celular.
- **Alterações de configuração de Wi-Fi**: escolha **Bloquear** para impedir que os usuários alterem as configurações de Wi-Fi criadas pelo proprietário do dispositivo. Os usuários podem criar suas próprias configurações de Wi-Fi. **Não configurado** permite que os usuários alterem as configurações de Wi-Fi no dispositivo.
- **Configuração do ponto de acesso Wi-Fi**: escolha **Bloquear** para impedir que os usuários criem ou alterem configurações de Wi-Fi. **Não configurado** permite que os usuários alterem as configurações de Wi-Fi no dispositivo.
- **Configuração de Bluetooth**: escolha **Bloquear** para impedir que os usuários configurem o Bluetooth no dispositivo. **Não configurado** permite usar o Bluetooth no dispositivo.
- **Compartilhamento de Internet e acesso a hotspots**: escolha **Bloquear** para impedir o compartilhamento de Internet e o acesso a hotspots portáteis. **Não configurado** permite o compartilhamento de Internet e o acesso a hotspots portáteis.
- **Armazenamento USB**: escolha **permitir** para acessar o armazenamento USB no dispositivo. **Não configurado** impede o acesso ao armazenamento USB.
- **Transferência de arquivos USB**: escolha **Bloquear** para impedir a transferência de arquivos por USB. **Não configurado** permite transferir arquivos.
- **Mídia externa**: escolha o **bloco** para impedir o uso ou a conexão de qualquer mídia externa no dispositivo. **Não configurado** permite a mídia externa no dispositivo.
- **Transmitir dados usando NFC**: escolha **Bloquear** para impedir o uso da tecnologia NFC (comunicação a curta distância) para transmitir dados de aplicativos. **Não configurado** permite o uso de NFC para compartilhar dados entre dispositivos.
- **Recursos de depuração**: escolha **permitir** para permitir que os usuários usem recursos de depuração no dispositivo. **Não configurado** impede que os usuários usem os recursos de depuração no dispositivo.
- **Ajuste do microfone**: escolha **Bloquear** para impedir que os usuários desfaçam o mudo do microfone e ajuste o volume do microfone. **Não configurado** permite que o usuário use e ajuste o volume do microfone no dispositivo.
- **Emails de proteção de redefinição de fábrica**: escolha **endereços de email da conta do Google**. Insira os endereços de email dos administradores do dispositivo que podem desbloquear o dispositivo depois que ele é apagado. Lembre-se de separar os endereços de email com um ponto-e-vírgula, como `admin1@gmail.com;admin2@gmail.com`. Se um email não for inserido, qualquer pessoa poderá desbloquear o dispositivo depois que ele for restaurado para as configurações de fábrica. Esses emails se aplicam somente quando uma redefinição de fábrica que não é de usuário é executada, como executar uma redefinição de fábrica usando o menu de recuperação.
- **Hachura de escape de rede**: escolha **habilitar** para permitir que os usuários ativem o recurso de hachura de escape de rede. Se uma conexão de rede não for feita quando o dispositivo for inicializado, a hachura de escape solicitará que se conecte temporariamente a uma rede e atualize a política do dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Esse recurso conectará os dispositivos a uma rede se:
  - Não há uma rede adequada na última política.
  - O dispositivo é inicializado em um aplicativo no modo de tarefa de bloqueio.
  - O usuário não pode acessar as configurações do dispositivo.

  **Não configurado** impede que os usuários ativem o recurso de hachura de escape de rede no dispositivo.

- **Atualização do sistema**: escolha uma opção para definir como o dispositivo lida com as atualizações ao longo do ar:
  - **Predefinição do Dispositivo**: utiliza a predefinição do dispositivo.
  - **Automático**: as atualizações são instaladas automaticamente sem interação do utilizador. Definir esta política imediatamente instala todas as atualizações pendentes.
  - **Adiado**: as atualizações são adiadas por 30 dias. No final dos 30 dias, o Android solicita que o usuário instale a atualização. É possível os fabricantes de dispositivos ou operadoras impedirem (isentarem) o adiamento de atualizações de segurança importantes. Uma atualização isenta mostra uma notificação de sistema ao utilizador no dispositivo. 
  - **Janela de manutenção**: as atualizações são instaladas automaticamente durante uma janela de manutenção diária definida no Intune. A instalação tenta diariamente por 30 dias e pode falhar se não houver espaço ou níveis de bateria suficientes. Após 30 dias, o Android solicita a instalação do usuário. Esta janela também é utilizada para instalar atualizações para aplicações do Play. Use essa opção para dispositivos dedicados, como quiosques, como aplicativos de primeiro plano de dispositivo dedicado de aplicativo único podem ser atualizados.

- **Janelas de notificação**: quando definido como **desabilitar**, as notificações de janela, incluindo solicitações de notificação, chamadas de entrada, chamadas de saída, alertas do sistema e erros do sistema não são mostradas no dispositivo. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode ser Mostrar notificações.
- **Ignorar dicas de primeiro uso**: escolha **habilitar** para ocultar ou ignorar sugestões de aplicativos para percorrer tutoriais ou ler dicas introdutórias quando o aplicativo for iniciado. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode ser mostrar essas sugestões quando o aplicativo é iniciado.

### <a name="system-security-settings"></a>Definições de segurança do sistema

- **Verificação de ameaças em aplicativos**: **exigir** (padrão) habilita Google Play proteger para verificar os aplicativos antes e depois que eles são instalados. Se detectar uma ameaça, ele poderá avisar o usuário para remover o aplicativo do dispositivo. **Não configurado** não habilita nem executa Google Play proteger para verificar aplicativos.

### <a name="dedicated-device-settings"></a>Configurações de dispositivo dedicado

Use essas configurações para configurar uma experiência em estilo de quiosque em seus dispositivos dedicados. Você pode configurar um dispositivo para executar um aplicativo ou executar muitos aplicativos. Quando um dispositivo é definido com o modo de quiosque, somente os aplicativos que você adiciona estão disponíveis. Essas configurações se aplicam a dispositivos Android Enterprise dedicados. Eles não se aplicam a dispositivos Android Enterprise totalmente gerenciados.

**Modo de quiosque**: escolha se o dispositivo executa um aplicativo ou executa vários aplicativos.

- **Aplicativo único**: os usuários só podem acessar um único aplicativo no dispositivo. Quando o dispositivo é iniciado, somente o aplicativo específico é iniciado. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

  - **Selecionar um aplicativo gerenciado**: selecione o aplicativo Google Play gerenciado na lista.

    Se você não tiver nenhum aplicativo listado, [adicione alguns aplicativos Android](../apps/apps-add-android-for-work.md) ao dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Ao usar o modo de quiosque de aplicativo único, os aplicativos de discagem/telefone podem não funcionar corretamente. 
  
- **Vários aplicativos**: os usuários podem acessar um conjunto limitado de aplicativos no dispositivo. Quando o dispositivo for iniciado, somente os aplicativos que você adicionar iniciarão. Você também pode adicionar alguns links da Web que os usuários podem abrir. Quando a política é aplicada, os usuários veem os ícones para os aplicativos permitidos na tela inicial.

  > [!IMPORTANT]
  > Para dispositivos dedicados de vários aplicativos, o [aplicativo de tela inicial gerenciado](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) da Google Play **deve ser**:
  >   - [Adicionado como um aplicativo cliente](../apps/apps-add-android-for-work.md) no Intune
  >   - [Atribuído ao grupo de dispositivos](../apps/apps-deploy.md) criado para seus dispositivos dedicados
  > 
  > O aplicativo de **tela inicial gerenciado** não precisa estar no perfil de configuração, mas é necessário adicioná-lo como um aplicativo cliente. Quando o aplicativo da **tela inicial gerenciada** é adicionado como um aplicativo cliente, todos os outros aplicativos adicionados no perfil de configuração são mostrados como ícones no aplicativo de **tela inicial gerenciado** . 
  >
  > Ao usar o modo de quiosque de vários aplicativos, os aplicativos de discagem/telefone podem não funcionar corretamente. 

  - **Adicionar**: selecione seus aplicativos na lista.

    Se o aplicativo de **tela inicial gerenciada** não estiver listado, [adicione-o de Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Certifique-se de [atribuir o aplicativo](../apps/apps-deploy.md) ao grupo de dispositivos criado para seus dispositivos dedicados.

    Você também pode adicionar outros [aplicativos Android](../apps/apps-add-android-for-work.md) e [aplicativos Web](../apps/web-app.md) criados por sua organização ao dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](../apps/apps-deploy.md).

  - **Botão página inicial virtual**: um botão de chave flexível que retorna usuários para a tela inicial gerenciada para que os usuários possam alternar entre aplicativos. As opções são:

    - **Não configurado** (padrão): um botão de página inicial não é mostrado. Os usuários devem usar o botão voltar para alternar entre aplicativos.
    - **Deslizar para cima**: um botão página inicial mostra quando um usuário passa o dedo para cima no dispositivo.
    - **Flutuante**: mostra um botão de página inicial persistente e flutuante no dispositivo.

  - **Sair do modo de quiosque**: escolha **habilitar** para permitir que os administradores pausem temporariamente o modo de quiosque para atualizar o dispositivo. Para usar esse recurso, o administrador:
  
    1. Continua selecionando o botão voltar até que o botão **sair do quiosque** seja mostrado. 
    2. Seleciona o botão **sair do quiosque** e entra no **código do modo de quiosque** de saída.
    3. Quando terminar, selecione o aplicativo de **tela inicial gerenciado** . Esta etapa rebloqueia o dispositivo no modo de quiosque de vários aplicativos.

      Quando definido como **não configurado**, os administradores não podem pausar o modo de quiosque. Se o administrador continuar selecionando o botão voltar e seleciona o botão **sair do quiosque** , uma mensagem informa que uma senha é necessária.

    - **Deixe o código do modo de quiosque**: Insira um PIN numérico de 4-6 dígitos. O administrador usa esse PIN para pausar temporariamente o modo de quiosque.

  - **Definir o plano de fundo da URL personalizada**: Insira uma URL para personalizar a tela de fundo no dispositivo dedicado.

    > [!NOTE]
    > Na maioria dos casos, é recomendável iniciar com imagens de pelo menos os seguintes tamanhos:
    >
    > - Telefone: 1080x1920 px
    > - Tablet: 1920 x 1080 px
    >
    > Para obter a melhor experiência e os detalhes nítidos, é recomendável que os ativos por imagem do dispositivo sejam criados para as especificações de exibição.
    >
    > Os monitores modernos têm densidades de pixel mais altas e podem exibir imagens de definição de 2K/4K equivalentes.

  - **Configuração de Wi-Fi**: **habilitar** mostra o controle Wi-Fi na tela inicial gerenciada e permite que os usuários finais conectem o dispositivo a redes wifi diferentes. Habilitar esse recurso também ativa o local do dispositivo. **Não configurado** (padrão) não mostra o controle Wi-Fi na tela inicial gerenciada. Ele impede que os usuários se conectem a redes Wi-Fi usando a tela inicial gerenciada.

  - **Configuração de Bluetooth**: **habilitar** mostra o controle Bluetooth na tela inicial gerenciada e permite que os usuários finais Emparelhem dispositivos via Bluetooth. Habilitar esse recurso também ativa o local do dispositivo. **Não configurado** (padrão) não mostra o controle Bluetooth na tela inicial gerenciada. Ele impede que os usuários configurem dispositivos Bluetooth e de emparelhamento ao usar a tela inicial gerenciada.

  - **Acesso à lanterna**: **habilitar** mostra o controle lanterna na tela inicial gerenciada e permite que os usuários finais ativem ou desativem a lanterna. **Não configurado** (padrão) não mostra o controle lanterna na tela inicial gerenciada. Ele impede que os usuários usem a lanterna ao usar a tela inicial gerenciada.

  - **Controle de volume de mídia**: **habilitar** mostra o controle de volume de mídia na tela inicial gerenciada e permite que os usuários finais ajustem o volume de mídia do dispositivo usando um controle deslizante. **Não configurado** (padrão) não mostra o controle de volume de mídia na tela inicial gerenciada. Ele impede que os usuários ajustem o volume de mídia do dispositivo ao usar a tela inicial gerenciada, a menos que seus botões de hardware ofereçam suporte a ele. 

  - **Modo de proteção de tela**: **habilitar** mostra uma barra de proteção na tela inicial gerenciada quando o dispositivo está bloqueado ou expira. **Não configurado** (padrão) não mostra uma barra de proteção na tela inicial gerenciada.

    Quando habilitado, configure também:

    - **Definir imagem de proteção de tela personalizada**: Insira a URL para uma imagem personalizada. Por exemplo, digite:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Se você não inserir uma URL, a imagem padrão do dispositivo será usada, se houver uma imagem padrão.

    - **Número de segundos que o dispositivo mostra a proteção de tela antes**de desligar a tela: escolha por quanto tempo o dispositivo mostra a proteção. Insira um valor entre 0-9999999 segundos. O padrão é `0` segundos. Quando deixado em branco ou definido como zero (`0`), a proteção de tela estará ativa até que um usuário interaja com o dispositivo.
    - **Número de segundos em que o dispositivo fica inativo antes de mostrar a proteção de tela**: escolha por quanto tempo o dispositivo estará ocioso antes de mostrar a proteção. Insira um valor entre 1-9999999 segundos. O padrão é `30` segundos. Você deve inserir um número maior que zero (`0`).
    - **Detectar mídia antes de iniciar a proteção de tela**: **habilitar** (padrão) não mostrará a proteção de tela se áudio ou vídeo estiver sendo reproduzido no dispositivo. **Não configurado** mostra a proteção de tela, mesmo se o áudio ou vídeo estiver sendo reproduzido.

### <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Desabilitar tela de bloqueio**: escolha **desabilitar** para impedir que os usuários usem o recurso de tela de bloqueio do keyguard no dispositivo. **Não configurado** permite que o usuário use os recursos do keyguard.
- **Recursos da tela de bloqueio desabilitados**: quando o keyguard está habilitado no dispositivo, escolha quais recursos serão desabilitados. Por exemplo, quando a **câmera segura** está marcada, o recurso de câmera é desabilitado no dispositivo. Todos os recursos não verificados estão habilitados no dispositivo.

  Esses recursos estão disponíveis para os usuários quando o dispositivo está bloqueado. Os usuários não verão nem acessarão os recursos que estão marcados.

- **Tipo de palavra-passe necessária**: define o tipo de palavra-passe necessária para o dispositivo. As opções são:
  - **Predefinição do dispositivo**
  - **Palavra-passe obrigatória, sem restrições**
  - Biometria fraco: a **biométrica** [forte versus fraca](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre o site do Android)
  - **Numeric**: a senha deve ser apenas números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Numérico complexo**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfabético**: as letras no alfabeto são obrigatórias. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico**: inclui letras maiúsculas, letras minúsculas e caracteres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico com símbolos**: inclui letras maiúsculas, letras minúsculas, caracteres numéricos, sinais de Pontuação e símbolos. Introduza também:

    - **Comprimento mínimo da senha**: Insira o comprimento mínimo que a senha deve ter, entre 4 e 16 caracteres.
    - **Número de caracteres necessários**: Insira o número de caracteres que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres minúsculos necessários**: Insira o número de caracteres minúsculos que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres maiúsculos necessários**: Insira o número de caracteres maiúsculos que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres que não são de letra necessários**: Insira o número de letras que não sejam maiúsculas (algo que não seja letras no alfabeto) que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres numéricos necessários**: Insira o número de caracteres numéricos (`1`, `2`, `3` e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres de símbolo necessários**: Insira o número de caracteres de símbolo (`&`, `#`, `%` e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.

- **Número de dias até a senha expirar**: Insira o número de dias, entre 1-365, até que a senha do dispositivo deva ser alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.
- **Número de senhas necessárias antes que o usuário possa resuse uma senha**: Insira o número de senhas recentes que não podem ser reutilizadas, entre 1-24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.
- **Número de falhas de entrada antes de apagar o dispositivo**: Insira o número, entre 4-11, de entradas com falha para permitir antes que o dispositivo seja apagado.

### <a name="power-settings"></a>Definições de energia

- **Tempo para bloquear ecrã**: define o período de tempo de inatividade necessário antes de o dispositivo ser bloqueado.
- **Ecrã ligado enquanto o dispositivo está ligado**: selecione que fontes de energia fazem com que o ecrã do dispositivo permaneça ligado enquanto o dispositivo está ligado.

### <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos utilizadores**: selecione **Bloquear** para impedir que os utilizadores adicionem novos utilizadores. Cada usuário tem um espaço pessoal no dispositivo para telas domésticas, contas, aplicativos e configurações personalizadas. **Não configurado** permite que os usuários adicionem outros usuários ao dispositivo.
- **Remoção do utilizador**: selecione **Bloquear** para impedir que os utilizadores removam utilizadores. **Não configurado** permite que os usuários removam outros usuários do dispositivo.
- **Alterações à conta**: selecione **Bloquear** para impedir que os utilizadores modifiquem as contas. **Não configurado** permite que os usuários atualizem contas de usuário no dispositivo.

  > [!NOTE]
  > Essa configuração não é respeitada em dispositivos de proprietário do dispositivo (totalmente gerenciado). Se você definir essa configuração, a configuração será ignorada e não terá nenhum impacto.

### <a name="applications"></a>Aplicações

- **Permitir instalação de fontes desconhecidas**: escolha **permitir** para que os usuários possam ativar **fontes desconhecidas**. Essa configuração permite que os aplicativos instalem de fontes desconhecidas, incluindo fontes diferentes da Google Play Store. **Não configurado** impede que os usuários ativem **fontes desconhecidas**.
- **Permitir acesso a todos os aplicativos na Google Play Store**: quando definido como **permitir**, os usuários obtêm acesso a todos os aplicativos na loja Google Play. Eles não obtêm acesso aos aplicativos que o administrador bloqueia em [aplicativos cliente](../apps/apps-add-android-for-work.md). **Não configurado** força os usuários a acessar apenas os aplicativos que o administrador disponibiliza Google Play armazenamento ou aplicativos necessários em [aplicativos cliente](../apps/apps-add-android-for-work.md).
- **Atualizações automáticas do aplicativo**: escolha quando as atualizações automáticas estão instaladas. As opções são:
  - **Não configurado**
  - **Escolha do usuário**
  - **Jamais**
  - **Somente Wi-Fi**
  - **Constante**

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
  > - Pode haver problemas conhecidos ao usar a VPN por aplicativo com acesso de F5 para Android 3.0.4. Consulte [se BigIP Release Notes for F5 Access for 3.0.4 Android](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="work-profile-only"></a>Apenas perfil de trabalho 

### <a name="work-profile-settings"></a>Definições de perfil de trabalho

#### <a name="general"></a>Geral

- **Copiar e colar entre perfis pessoais e de trabalho**: escolha **Bloquear** para evitar copiar e colar entre aplicativos pessoais e de trabalho. **Não configurado** permite que os usuários compartilhem dados usando copiar e colar com aplicativos no perfil pessoal 
- **Compartilhamento de dados entre perfis pessoais e de trabalho**: escolha se os aplicativos no perfil de trabalho podem compartilhar com aplicativos no perfil pessoal. Por exemplo, você pode controlar ações de compartilhamento em aplicativos, como o **compartilhamento...** na aplicação do browser Chrome. Esta definição não se aplica ao comportamento da área de transferência de copiar/colar. Suas opções de compartilhamento:
  - **Restrições de partilha predefinidas**: o comportamento de partilha predefinido do dispositivo, que varia consoante a versão do Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. Em dispositivos com a versão 6.0 e versões posteriores, a Google não bloqueia a partilha do perfil pessoal para o perfil de trabalho.
  - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal**: ativa a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Permitir partilha entre limites**: ativa a partilha entre limites do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Esta definição permite que aplicações geridas no perfil de trabalho partilhem com aplicações no lado não gerido do dispositivo. Por isso, utilize esta definição com cuidado.

- **Notificações de perfil de trabalho enquanto o dispositivo está bloqueado**: controla se os aplicativos no perfil de trabalho podem mostrar dados em notificações quando o dispositivo está bloqueado. O **bloco** não mostra os dados. **Não configurado** mostra os dados.
- **Permissões de aplicações predefinidas**: define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Utilize esta política para conceder permissões automaticamente sem aviso, recusar permissões automaticamente sem aviso ou permitir que o utilizador final decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

  Também pode utilizar uma política de Configuração de Aplicações para conceder permissões a aplicações individuais (**Aplicações Cliente** > **Políticas de configuração da aplicação**).

- **Adicionar e remover contas**: escolha **Bloquear** para impedir que os usuários finais adicionem ou removam contas manualmente no perfil de trabalho. Por exemplo, ao implementar a aplicação Gmail num perfil de trabalho do Android, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho. **Não configurado** permite adicionar contas no perfil de trabalho.  

- **Partilha de contactos por Bluetooth**: permite aceder aos contactos do trabalho a partir de outro dispositivo, como um automóvel, que esteja emparelhado através de Bluetooth. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Ativar esta definição pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura de tela**: escolha **Bloquear** para impedir capturas de tela ou capturas de telas no dispositivo no perfil de trabalho. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite obter capturas de tela.

- **Exibir ID do chamador do contato comercial no perfil pessoal**: quando habilitado (**não configurado**), os detalhes do chamador de contato de trabalho são exibidos no perfil pessoal. Quando definido como **Bloquear**, o número do chamador de contato de trabalho não é exibido no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Pesquisar contatos de trabalho do perfil pessoal**: escolha **Bloquear** para impedir que os usuários pesquisem contatos de trabalho em aplicativos no perfil pessoal. **Não obrigatório** permite pesquisar contatos de trabalho no perfil pessoal.

- **Câmera**: escolha **Bloquear** para impedir o acesso à câmera no dispositivo no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição. **Não obrigatório** permite o acesso à câmera no perfil de trabalho.

- **Permitir widgets de aplicativos de perfil de trabalho**: **habilitar** permite que os usuários finais coloquem widgets expostos por aplicativos na tela inicial. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

  Por exemplo, o Outlook é instalado nos perfis de trabalho de seus usuários. Quando definido como **habilitar**, os usuários podem colocar o widget pauta na tela inicial do dispositivo.

#### <a name="work-profile-password"></a>Senha do perfil de trabalho

- **Exigir Palavra-passe de Perfil de Trabalho**: aplica-se ao Android 7.0 e posterior com o perfil de trabalho ativado. Escolha **exigir** para inserir uma política de senha que se aplica somente aos aplicativos no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois. **Não configurado** permite que o usuário use aplicativos de trabalho, sem inserir uma senha.
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
- **Desbloqueio de impressão digital**: escolha **Bloquear** para impedir que os usuários finais usem o scanner de impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite que os usuários desbloqueiem dispositivos com uma impressão digital no perfil de trabalho.
- **Smart Lock e outros agentes de confiança**: escolha **Bloquear** para impedir que Smart Lock ou outros agentes de confiança ajustem as configurações da tela de bloqueio em dispositivos compatíveis. Esse recurso, às vezes conhecido como agente de confiança, permite desabilitar ou ignorar a senha da tela de bloqueio do dispositivo se o dispositivo estiver em um local confiável. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="device-password"></a>Palavra-passe do dispositivo

Essas configurações de senha se aplicam a perfis pessoais em dispositivos que usam um perfil de trabalho.

- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter, de **4**-**14**.
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de todos os dados do dispositivo serem eliminados
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
- **Desbloqueio de impressão digital**: escolha **Bloquear** para impedir que o usuário final use o scanner de impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de confiança**: escolha **Bloquear** para impedir que Smart Lock ou outros agentes de confiança ajustem as configurações da tela de bloqueio em dispositivos compatíveis. Esse recurso, às vezes conhecido como agente de confiança, permite desabilitar ou ignorar a senha da tela de bloqueio do dispositivo se o dispositivo estiver em um local confiável. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="system-security"></a>Segurança do sistema

- **Verificação de ameaças em aplicativos**: **exige** a aplicação de que a configuração **verificar aplicativos** está habilitada para perfis pessoais e de trabalho.

   > [!Note]
   > Esta definição só funciona para dispositivos Android O e posteriores.

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
  > - Pode haver problemas conhecidos ao usar a VPN por aplicativo com acesso de F5 para Android 3.0.4. Consulte [se BigIP Release Notes for F5 Access for 3.0.4 Android](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de quiosque de dispositivo dedicados para dispositivos [Android](device-restrictions-android.md#kiosk) e [Windows 10](kiosk-settings.md) .

## <a name="see-also"></a>Consulte também

[Configurando e Solucionando problemas de dispositivos Android Enterprise no Microsoft Intune](https://support.microsoft.com/help/4476974)
