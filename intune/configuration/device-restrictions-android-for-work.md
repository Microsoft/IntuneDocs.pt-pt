---
title: Definições de dispositivos empresariais Android no Microsoft Intune – Azure | Documentos da Microsoft
description: Em dispositivos Android Enterprise ou Android for Work, restrinja as configurações no dispositivo, incluindo copiar e colar, Mostrar notificações, permissões de aplicativo, compartilhamento de dados, comprimento da senha, falhas de conexão, usar impressão digital para desbloquear, reutilizar senhas e habilitar Bluetooth compartilhamento de contatos de trabalho. Configure dispositivos como um quiosque de dispositivo dedicado para executar um aplicativo ou vários aplicativos.
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
ms.openlocfilehash: b6afd80517df3496e0c1402fc0c76f3fc24969fa
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206606"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos do Android Enterprise para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, executar aplicativos em dispositivos dedicados, controlar a segurança e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

Essas configurações se aplicam a tipos de registro do Android Enterprise, em que o Intune controla todo o dispositivo, como dispositivos Android Enterprise totalmente gerenciados ou dedicados.

### <a name="general-settings"></a>Definições gerais

- **Captura de ecrã**: escolha **bloco** para impedir capturas de ecrã ou ecrã capturas no dispositivo. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Câmara**: escolha **bloco** para impedir o acesso à câmara do dispositivo. **Não é necessário** permite o acesso à câmara do dispositivo.
- **Política de permissões predefinida**: esta definição configura a política de permissões predefinida para pedidos de permissões de runtime. Os valores possíveis incluem:
  - **Predefinição do dispositivo**: utiliza a predefinição do dispositivo.
  - **Pedir**: é pedido ao utilizador que aprove a permissão.
  - **Conceder automaticamente**: as permissões são concedidas automaticamente.
  - **Negar automaticamente**: as permissões são negadas automaticamente.
- **Alterações de data e hora**: escolha **bloco** para impedir que os utilizadores, desde a configuração manualmente a data e hora. **Não configurado** permite aos utilizadores para a data definida e a hora no dispositivo.
- **Alterações de volume**: o **bloco** impede que os usuários alterem o volume do dispositivo e também faz mudo do volume mestre. **Não configurado** permite utilizando as definições de volume no dispositivo.
- **Reposição de fábrica**: escolha **bloco** para impedir que os utilizadores com o factory reposição opção nas definições do dispositivo. **Não configurado** permite aos utilizadores utilizar esta definição no dispositivo.
- **Arranque seguro**: selecione **Bloquear** para impedir que os utilizadores reiniciem o dispositivo em modo de segurança. **Não configurado** permite aos utilizadores reiniciar o dispositivo em modo de segurança.
- **Barra de status**: escolha **bloco** para impedir o acesso a barra de estado, incluindo notificações e definições rápidas. **Não configurado** permite aos utilizadores acesso a barra de status.
- **Serviços de dados de roaming**: escolha **bloco** para impedir que os dados em roaming na rede celular. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **As alterações de definições de Wi-Fi**: escolha **bloco** para impedir que os utilizadores alterem as definições de Wi-Fi criadas pelo proprietário do dispositivo. Os utilizadores podem criar suas próprias configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração de ponto de acesso Wi-Fi**: escolha **bloco** para impedir que os utilizadores a criar ou alterar quaisquer configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração de Bluetooth**: escolha **bloco** para impedir que os utilizadores configurem Bluetooth no dispositivo. **Não configurado** permite o uso de Bluetooth no dispositivo.
- **Tethering e acesso a pontos ativos**: escolha **bloco** para impedir que tethering e acesso a pontos ativos portátil. **Não configurado** permite tethering e acesso a pontos ativos portátil.
- **Armazenamento USB**: escolha **permitir** para o armazenamento USB de acesso no dispositivo. **Não configurado** impede o acesso a armazenamento USB.
- **Transferência de ficheiros USB**: escolha **bloco** para impedir a transferência de ficheiros através de USB. **Não configurado** permite a transferência de ficheiros.
- **Suporte de dados externo**: escolha **bloco** para impedir a utilizar ou ligar a qualquer suporte de dados externo no dispositivo. **Não configurado** permite o suporte de dados externo no dispositivo.
- **Feixe dados através de NFC**: escolha **bloco** para impedir a utilização da tecnologia de junto ao campo comunicação (NFC) a feixe dados a partir de aplicações. **Não configurado** permite o uso de NFC para partilhar dados entre dispositivos.
- **Recursos de depuração**: escolha **permitir** para permitir que os utilizadores utilizem os recursos de depuração no dispositivo. **Não configurado** impede que os usuários usando os recursos de depuração no dispositivo.
- **Ajuste do microfone**: escolha **bloco** para impedir que os utilizadores de ativação do som do microfone e ajustar o volume do microfone. **Não configurado** permite ao utilizador utilizar e ajustar o volume do microfone do dispositivo.
- **E-mails de proteção de reposição de fábrica**: escolha **endereços de e-mail de conta Google**. Introduza os endereços de e-mail dos administradores de dispositivos que possam desbloquear o dispositivo depois de serem eliminado. Certifique-se de que separe os endereços de e-mail com ponto e vírgula, por exemplo, `admin1@gmail.com;admin2@gmail.com`. Se uma mensagem de e-mail não é inserida, qualquer pessoa pode desbloquear o dispositivo após o restauro para as definições de fábrica. Esses emails se aplicam somente quando uma redefinição de fábrica que não é de usuário é executada, como executar uma redefinição de fábrica usando o menu de recuperação.
- **Saída de emergência da rede**: escolha **ativar** para permitir que os utilizadores ativar a funcionalidade de Sombreado traçado de escape de rede. Se uma conexão de rede não é feita quando o dispositivo for arrancado, a saída de emergência pede para temporariamente ligar a uma rede e atualizar a política de dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Esta funcionalidade liga dispositivos a uma rede se:
  - Não existe uma rede adequada na política de última.
  - O dispositivo for arrancado numa aplicação no modo de bloqueio de tarefa.
  - O utilizador é não é possível alcançar as definições do dispositivo.

  **Não configurado** impede que os utilizadores de ativarem a funcionalidade de Sombreado traçado de escape de rede no dispositivo.

- **Atualização do sistema**: escolher uma opção para definir a forma como o dispositivo processa atualizações por ondas eletromagnéticas:
  - **Predefinição do Dispositivo**: utiliza a predefinição do dispositivo.
  - **Automático**: as atualizações são instaladas automaticamente sem interação do utilizador. Definir esta política imediatamente instala todas as atualizações pendentes.
  - **Adiado**: as atualizações são adiadas por 30 dias. No final dos 30 dias, o Android solicita ao utilizador para instalar a atualização. É possível os fabricantes de dispositivos ou operadoras impedirem (isentarem) o adiamento de atualizações de segurança importantes. Uma atualização isenta mostra uma notificação de sistema ao utilizador no dispositivo.
  - **Janela de manutenção**: as atualizações são instaladas automaticamente durante uma janela de manutenção diária definida no Intune. Instalação tenta diariamente durante 30 dias e pode falhar se houver níveis insuficientes de espaço ou útil da bateria. Após 30 dias, o Android solicita ao utilizador que instalar. Esta janela também é utilizada para instalar atualizações para aplicações do Play. Use essa opção para dispositivos dedicados, como quiosques, como aplicativos de primeiro plano de dispositivo dedicado de aplicativo único podem ser atualizados.

- **Janelas de notificação**: quando definido como **desabilitar**, as notificações de janela, incluindo solicitações de notificação, chamadas de entrada, chamadas de saída, alertas do sistema e erros do sistema não são mostradas no dispositivo. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode ser Mostrar notificações.
- **Ignorar dicas de primeiro uso**: **habilitar** oculta ou ignora sugestões de aplicativos que percorrem tutoriais ou dicas quando o aplicativo é iniciado. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode mostrar essas sugestões quando o aplicativo é iniciado.

### <a name="system-security-settings"></a>Definições de segurança do sistema

- **Verificação de ameaças em aplicativos**: **exigir** (padrão) habilita Google Play proteger para verificar os aplicativos antes e depois que eles são instalados. Se detectar uma ameaça, ele poderá avisar o usuário para remover o aplicativo do dispositivo. **Não configurado** não habilita nem executa Google Play proteger para verificar aplicativos.

### <a name="dedicated-device-settings"></a>Configurações de dispositivo dedicado

Use essas configurações para configurar uma experiência em estilo de quiosque em seus dispositivos dedicados. Você pode configurar um dispositivo para executar um aplicativo ou executar muitos aplicativos. Quando um dispositivo é definido com o modo de quiosque, somente os aplicativos que você adiciona estão disponíveis. Essas configurações se aplicam a dispositivos Android Enterprise dedicados. Eles não se aplicam a dispositivos Android Enterprise totalmente gerenciados.

**Modo de quiosque**: escolha se o dispositivo executa um aplicativo ou executa vários aplicativos.

- **Aplicativo único**: os usuários só podem acessar um único aplicativo no dispositivo. Quando o dispositivo é iniciado, apenas a aplicação específica é iniciada. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

  - **Selecionar um aplicativo gerenciado**: selecione o aplicativo Google Play gerenciado na lista.

    Se não tiver todas as aplicações listadas, em seguida, [adicionar algumas aplicações Android](../apps/apps-add-android-for-work.md) no dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Ao usar o modo de quiosque de aplicativo único, os aplicativos de discagem/telefone podem não funcionar corretamente. 
  
- **Vários aplicativos**: os usuários podem acessar um conjunto limitado de aplicativos no dispositivo. Quando o dispositivo é iniciado, inicie apenas as aplicações que adicionar. Também pode adicionar alguns links da web que os utilizadores podem abrir. Quando a política é aplicada, os utilizadores veem ícones para aplicações permitidas na tela inicial.

  > [!IMPORTANT]
  > Para dispositivos dedicados de vários aplicativos, o [aplicativo de tela inicial gerenciado](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) da Google Play **deve ser**:
  >   - [Adicionado como uma aplicação de cliente](../apps/apps-add-android-for-work.md) no Intune
  >   - [Atribuído ao grupo de dispositivos](../apps/apps-deploy.md) criado para seus dispositivos dedicados
  >
  > O **geridos tela home page** aplicação não é necessário para estar no perfil de configuração, mas é necessário para ser adicionado como uma aplicação de cliente. Quando o aplicativo da **tela inicial gerenciada** é adicionado como um aplicativo cliente, todos os outros aplicativos adicionados no perfil de configuração são mostrados como ícones no aplicativo de **tela inicial gerenciado** .
  >
  > Ao usar o modo de quiosque de vários aplicativos, os aplicativos de discagem/telefone podem não funcionar corretamente. 

  - **Adicionar**: selecione seus aplicativos na lista.

    Se o **geridos tela home page** aplicação não estiver listada, em seguida, [adicioná-lo a partir do Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Certifique-se de [atribuir o aplicativo](../apps/apps-deploy.md) ao grupo de dispositivos criado para seus dispositivos dedicados.

    Também pode adicionar outros [aplicações Android](../apps/apps-add-android-for-work.md) e [aplicações web](../apps/web-app.md) criados pela sua organização para o dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](../apps/apps-deploy.md).

  - **Botão página inicial virtual**: um botão de chave flexível que retorna usuários para a tela inicial gerenciada para que os usuários possam alternar entre aplicativos. As opções são:

    - **Não configurado** (padrão): um botão de página inicial não é mostrado. Os usuários devem usar o botão voltar para alternar entre aplicativos.
    - **Deslizar para cima**: um botão página inicial mostra quando um usuário passa o dedo para cima no dispositivo.
    - **Flutuante**: mostra um botão de página inicial persistente e flutuante no dispositivo.

  - **Saia do modo de local público**: escolha **ativar** para permitir aos administradores interromper temporariamente o modo de local público para atualizar o dispositivo. Para usar esse recurso, o administrador:
  
    1. Continua selecionando o botão voltar até que o botão **sair do quiosque** seja mostrado. 
    2. Seleciona o botão **sair do quiosque** e entra no **código do modo de quiosque** de saída.
    3. Quando terminar, selecione o aplicativo de **tela inicial gerenciado** . Este passo relocks o dispositivo em modo de local público de várias aplicações.

      Quando definido como **não configurado**, os administradores não podem pausar o modo de quiosque. Se o administrador continuar selecionando o botão voltar e seleciona o botão **sair do quiosque** , uma mensagem informa que uma senha é necessária.

    - **Deixe o código do modo de local público**: introduza um dígito de 4 a 6 PIN numérico. O administrador utiliza este PIN para interromper temporariamente o modo de local público.

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

    - **Definir imagem de proteção de tela personalizada**: Insira a URL para um png personalizado, jpg, JPEG, GIF, BMP, WebP ou ICOimage. Por exemplo, digite:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      Se você não inserir uma URL, a imagem padrão do dispositivo será usada, se houver uma imagem padrão.
      
      > [!TIP]
      > Qualquer URL de recurso de arquivo que possa ser transformada em um bitmap é suportada.

    - **Número de segundos que o dispositivo mostra a proteção de tela antes**de desligar a tela: escolha por quanto tempo o dispositivo mostra a proteção. Insira um valor entre 0-9999999 segundos. O padrão é `0` segundos. Quando deixado em branco ou definido como zero (`0`), a proteção de tela estará ativa até que um usuário interaja com o dispositivo.
    - **Número de segundos em que o dispositivo fica inativo antes de mostrar a proteção de tela**: escolha por quanto tempo o dispositivo estará ocioso antes de mostrar a proteção. Insira um valor entre 1-9999999 segundos. O padrão é `30` segundos. Você deve inserir um número maior que zero (`0`).
    - **Detectar mídia antes de iniciar a proteção de tela**: **habilitar** (padrão) não mostrará a proteção de tela se áudio ou vídeo estiver sendo reproduzido no dispositivo. **Não configurado** mostra a proteção de tela, mesmo se o áudio ou vídeo estiver sendo reproduzido.

### <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Desabilitar tela de bloqueio**: escolha **desabilitar** para impedir que os usuários usem o recurso de tela de bloqueio do keyguard no dispositivo. **Não configurado** permite que o usuário a usar os recursos de Keyguard.
- **Recursos da tela de bloqueio desabilitados**: quando o keyguard está habilitado no dispositivo, escolha quais recursos serão desabilitados. Por exemplo, quando a **câmera segura** está marcada, o recurso de câmera é desabilitado no dispositivo. Todos os recursos não verificados estão habilitados no dispositivo.

  Esses recursos estão disponíveis para os usuários quando o dispositivo está bloqueado. Os usuários não verão nem acessarão os recursos que estão marcados.

- **Tipo de palavra-passe necessária**: define o tipo de palavra-passe necessária para o dispositivo. As opções são:
  - **Predefinição do dispositivo**
  - **Palavra-passe obrigatória, sem restrições**
  - Biometria fraco: a **biométrica** [forte versus fraca](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre o site do Android)
  - **Numeric**: a senha deve ser apenas números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Complexo numérico**: números repetidos ou consecutivos, como "1111" ou "1234", não são permitidos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfabético**: as letras no alfabeto são obrigatórias. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico**: inclui letras maiúsculas, letras minúsculas e caracteres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérico com símbolos**: inclui letras maiúsculas, letras minúsculas, caracteres numéricos, sinais de Pontuação e símbolos. Introduza também:

    - **Comprimento mínimo da senha**: Insira o comprimento mínimo que a senha deve ter, entre 4 e 16 caracteres.
    - **Número de caracteres necessários**: Insira o número de caracteres que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres minúsculos necessários**: Insira o número de caracteres minúsculos que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres maiúsculos necessários**: Insira o número de caracteres maiúsculos que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres que não são de letra necessários**: Insira o número de letras que não sejam maiúsculas (algo que não seja letras no alfabeto) que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres numéricos necessários**: Insira o número de caracteres numéricos (`1`, `2`, `3`e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.
    - **Número de caracteres de símbolo necessários**: Insira o número de caracteres de símbolo (`&`, `#`, `%`e assim por diante) que a senha deve ter, entre 0 e 16 caracteres.

- **Número de dias até a senha expirar**: Insira o número de dias, entre 1-365, até que a senha do dispositivo deva ser alterada. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.
- **Número de senhas necessárias antes que o usuário possa resuse uma senha**: Insira o número de senhas recentes que não podem ser reutilizadas, entre 1-24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.
- **Número de falhas de entrada antes de apagar o dispositivo**: Insira o número, entre 4-11, de entradas com falha para permitir antes que o dispositivo seja apagado.

### <a name="power-settings"></a>Definições de energia

- **Tempo para bloquear a tela**: Insira o tempo máximo que um usuário pode definir até que o dispositivo seja bloqueado. Por exemplo, se você definir essa configuração como **10 minutos**, os usuários poderão definir o tempo de 15 segundos até 10 minutos. Quando definido como **não configurado** (padrão), o Intune não altera nem controla essa configuração.

- **Ecrã ligado enquanto o dispositivo está ligado**: selecione que fontes de energia fazem com que o ecrã do dispositivo permaneça ligado enquanto o dispositivo está ligado.

### <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos utilizadores**: selecione **Bloquear** para impedir que os utilizadores adicionem novos utilizadores. Cada utilizador tem um espaço pessoal no dispositivo para personalizado Home ecrãs, contas, aplicações e definições. **Não configurado** (padrão) permite que os usuários adicionem outros usuários ao dispositivo.
- **Remoção do utilizador**: selecione **Bloquear** para impedir que os utilizadores removam utilizadores. **Não configurado** (padrão) permite que os usuários removam outros usuários do dispositivo.
- **Alterações de conta** (somente dispositivos dedicados): escolha **Bloquear** para impedir que os usuários modifiquem contas. **Não configurado** (padrão) permite que os usuários atualizem contas de usuário no dispositivo.

  > [!NOTE]
  > Essa configuração não é respeitada em dispositivos de proprietário do dispositivo (totalmente gerenciado). Se você definir essa configuração, a configuração será ignorada e não terá nenhum impacto.

- O **usuário pode configurar credenciais**: **Bloquear** impede que os usuários configurem certificados atribuídos a dispositivos, até mesmo dispositivos que não estão associados a uma conta de usuário. **Não configurado** pode possibilitar que os usuários configurem ou alterem suas credenciais ao acessá-las no keystore. 
- **Contas pessoais do Google**: **Bloquear** impede que os usuários adicionem sua conta pessoal do Google ao dispositivo. **Não configurado** (padrão) permite que os usuários adicionem sua conta pessoal do Google.

### <a name="applications"></a>Aplicações

- **Permitir instalação de fontes desconhecidas**: escolha **permitir** para que os usuários possam ativar **fontes desconhecidas**. Essa configuração permite que os aplicativos instalem de fontes desconhecidas, incluindo fontes diferentes da Google Play Store. **Não configurado** impede que os utilizadores de ativarem **origens desconhecidas**.
- **Permitir acesso a todos os aplicativos na Google Play Store**: quando definido como **permitir**, os usuários obtêm acesso a todos os aplicativos na loja Google Play. Eles não obtêm acesso aos aplicativos que o administrador bloqueia em [aplicativos cliente](../apps/apps-add-android-for-work.md). **Não configurado** força os usuários a acessar apenas os aplicativos que o administrador disponibiliza Google Play armazenamento ou aplicativos necessários em [aplicativos cliente](../apps/apps-add-android-for-work.md).
- **É atualizado automaticamente a aplicação**: escolha quando instalar as atualizações automáticas. As opções são:
  - **Não configurado**
  - **Preferência de utilizador**
  - **Nunca**
  - **Apenas Wi-Fi**
  - **Sempre**

### <a name="connectivity"></a>Conectividade

- **VPN always-on**: selecione **Ativar** para definir um cliente VPN para se ligar e voltar a ligar à VPN automaticamente. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de implantar apenas uma política de VPN AlwaysOn em um único dispositivo. Não há suporte para a implantação de várias políticas de VPN AlwaysOn em um único dispositivo.

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
  > - Você ainda precisa configurar o cliente VPN com um [perfil VPN](vpn-settings-android-enterprise.md)ou por meio de um [perfil de configuração de aplicativo](../apps/app-configuration-policies-use-android.md).
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

- **Proxy global recomendado**: escolha **habilitar** para adicionar um proxy global aos dispositivos. Quando habilitado, o tráfego HTTP e HTTPS, incluindo alguns aplicativos no dispositivo, use o proxy que você inserir. Esse proxy é apenas uma recomendação. É possível que alguns aplicativos não usem o proxy. **Não configurado** (padrão) não adiciona um proxy global recomendado.

  Para obter mais informações sobre esse recurso, consulte [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)) (abre um site do Android).

  Quando habilitado, insira também o **tipo** de proxy. As opções são:

  - **Direto**: escolha esta opção para inserir manualmente os detalhes do servidor proxy, incluindo:
    - **Host**: Insira o nome de host ou endereço IP do seu servidor proxy. Por exemplo, introduza: `proxy.contoso.com` ou `127.0.0.1`.
    - **Número da porta**: Insira o número da porta TCP usada pelo servidor proxy. Por exemplo, introduza `8080`.
    - **Hosts excluídos**: Insira uma lista de nomes de host ou endereços IP que não usarão o proxy. Essa lista pode incluir um asterisco (`*`) curinga e vários hosts separados por ponto e vírgula (`;`) sem espaços. Por exemplo, introduza `127.0.0.1;web.contoso.com;*.microsoft.com`.

  - **Configuração automática de proxy**: Insira a **URL de PAC** para um script de configuração de proxy automático. Por exemplo, introduza `https://proxy.contoso.com/proxy.pac`.

    Para obter mais informações sobre arquivos PAC, consulte o [Arquivo PAC (configuração automática de proxy)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (abre um site que não é da Microsoft).

## <a name="work-profile-only"></a>Apenas perfil de trabalho

Essas configurações se aplicam a tipos de registro do Android Enterprise, em que o Intune controla somente o perfil de trabalho, como o registro de perfil de trabalho do Android Enterprise em um dispositivo pessoal ou BYOD (Traga seu próprio serviço).

### <a name="work-profile-settings"></a>Definições de perfil de trabalho

#### <a name="general"></a>Geral

- **Copiar e colar entre perfis pessoais e de trabalho**: escolha **bloco** para impedir a copiar e colar entre aplicações pessoais e de trabalho. **Não configurado** permite aos utilizadores partilhar dados através de copiar e colar com aplicações no perfil pessoal 
- **Partilha de dados entre perfis pessoais e de trabalho**: Escolha se as aplicações no perfil de trabalho podem partilhar com aplicações no perfil pessoal. Por exemplo, pode controlar ações compartilhamento em aplicativos, como o **partilha...** na aplicação do browser Chrome. Esta definição não se aplica ao comportamento da área de transferência de copiar/colar. As opções de partilha:
  - **Padrão do dispositivo**: o comportamento de compartilhamento padrão do dispositivo, que varia dependendo da versão do Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. Em dispositivos com a versão 6.0 e versões posteriores, a Google não bloqueia a partilha do perfil pessoal para o perfil de trabalho.
  - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal**: ativa a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Impedir qualquer compartilhamento entre limites**: impede o compartilhamento entre perfis pessoais e de trabalho.
  - **Sem restrições no compartilhamento**: habilita o compartilhamento entre o limite do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Esta definição permite que aplicações geridas no perfil de trabalho partilhem com aplicações no lado não gerido do dispositivo. Por isso, utilize esta definição com cuidado.

- **Notificações do perfil de trabalho, enquanto o dispositivo está bloqueado**: controla se a aplicações no perfil de trabalho podem mostrar dados em notificações quando o dispositivo está bloqueado. **Bloco** não mostra os dados. **Não configurado** mostra os dados.
- **Permissões de aplicações predefinidas**: define a política de permissões predefinida para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Utilize esta política para conceder permissões automaticamente sem aviso, recusar permissões automaticamente sem aviso ou permitir que o utilizador final decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

  Também pode utilizar uma política de Configuração de Aplicações para conceder permissões a aplicações individuais (**Aplicações Cliente** > **Políticas de configuração da aplicação**).

- **Adicionar e remover contas**: escolha **bloco** para impedir que os utilizadores finais de adicionarem ou removerem contas no perfil de trabalho manualmente. Por exemplo, ao implementar a aplicação Gmail num perfil de trabalho do Android, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho. **Não configurado** permite adicionar contas no perfil de trabalho.  

  > [!NOTE]
  > As contas do Google não podem ser adicionadas a um perfil de trabalho.

- **Partilha de contactos por Bluetooth**: permite aceder aos contactos do trabalho a partir de outro dispositivo, como um automóvel, que esteja emparelhado através de Bluetooth. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Ativar esta definição pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura de ecrã**: escolha **bloco** para impedir capturas de ecrã ou capturas do dispositivo no perfil de trabalho de ecrã. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite obter capturas de ecrã.

- **Apresentar id contacto de trabalho autor da chamada no perfil pessoal**: quando ativada (**não configurado**), os detalhes de contacto autor da chamada de trabalho são apresentados no perfil pessoal. Quando definido como **bloco**, o número de contacto autor da chamada do trabalho não for apresentado no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Pesquisar contactos de trabalho do perfil pessoal**: escolha **bloco** para impedir que os utilizadores a procurar contactos de trabalho nas aplicações no perfil pessoal. **Não é necessário** permite procurar contactos de trabalho no perfil pessoal.

- **Câmara**: escolha **bloco** para impedir o acesso à câmara do dispositivo no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição. **Não é necessário** permite o acesso à câmara no perfil de trabalho.

- **Permitir widgets de aplicativos de perfil de trabalho**: **habilitar** permite que os usuários finais coloquem widgets expostos por aplicativos na tela inicial. A opção **Não configurado** (predefinição) desativa esta funcionalidade.

  Por exemplo, o Outlook é instalado nos perfis de trabalho de seus usuários. Quando definido como **habilitar**, os usuários podem colocar o widget pauta na tela inicial do dispositivo.

#### <a name="work-profile-password"></a>Palavra-passe de perfil de trabalho

- **Exigir Palavra-passe de Perfil de Trabalho**: aplica-se ao Android 7.0 e posterior com o perfil de trabalho ativado. Escolher **requerem** para introduzir uma política de código de acesso que aplica-se apenas às aplicações no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois. **Não configurado** permite ao utilizador utilizar aplicações de trabalho, sem introduzir uma palavra-passe.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter, de **4**-**16**.
- **Máximo de minutos de inatividade até ao bloqueio do perfil de trabalho**: selecione a quantidade de tempo antes de o perfil de trabalho ser bloqueado. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de o perfil de trabalho do dispositivo ser eliminado.
- **Expiração da palavra-passe (dias)**: introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**).
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
- **Desbloqueio por impressão digital**: escolha **bloco** e impedir que os utilizadores finais utilizem a impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite aos utilizadores desbloquear os dispositivos com uma impressão digital no perfil de trabalho.
- **Smart Lock e outros agentes de fidedignidade**: escolha **bloco** para impedir que o Smart Lock ou outros agentes de fidedignidade de ajustarem as definições de ecrã de bloqueio em dispositivos compatíveis. Esse recurso, também conhecido como agente de confiança, permite desabilitar ou ignorar a senha da tela de bloqueio do dispositivo se o dispositivo estiver em um local confiável. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="device-password"></a>Palavra-passe do dispositivo

Estas definições de palavra-passe aplicam-se aos perfis pessoais nos dispositivos que utilizam um perfil de trabalho.

- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de carateres que a palavra-passe do utilizador tem de ter, de **4**-**14**.
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado
- **Número de falhas de início de sessão antes de limpar o dispositivo**: introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de todos os dados do dispositivo serem eliminados
- **Expiração da palavra-passe (dias)**: introduza o número de dias até ser preciso alterar a palavra-passe do utilizador final (**1**-**255**)
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
- **Desbloqueio por impressão digital**: escolha **bloco** para impedir que o utilizador final utilizar a impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de fidedignidade**: escolha **bloco** para impedir que o Smart Lock ou outros agentes de fidedignidade de ajustarem as definições de ecrã de bloqueio em dispositivos compatíveis. Esse recurso, também conhecido como agente de confiança, permite desabilitar ou ignorar a senha da tela de bloqueio do dispositivo se o dispositivo estiver em um local confiável. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="system-security"></a>Segurança do sistema

- **Análise de ameaças nas aplicações**: **requerem** impõe que o **verificar aplicações** definição está ativada para o trabalho e perfis pessoais.

   > [!Note]
   > Essa configuração só funciona para dispositivos que são Android 8 (Oreo) e superior.

- **Impedir instalações de aplicativos de fontes desconhecidas no perfil pessoal**: por design, os dispositivos Android Enterprise Work Profile não podem instalar aplicativos de fontes diferentes da Play Store. Por natureza, os dispositivos de perfil de trabalho devem ser de perfil duplo:

  - Um perfil de trabalho gerenciado usando o MDM.
  - Um perfil pessoal isolado do gerenciamento de MDM.

  Essa configuração permite que os administradores tenham mais controle das instalações de aplicativos de fontes desconhecidas. **Não configurado** (padrão) permite instalações de aplicativos de fontes desconhecidas no perfil pessoal. **Bloquear** impede instalações de aplicativos de fontes diferentes da Play Store no perfil pessoal.

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
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de quiosque de dispositivo dedicados para dispositivos [Android](device-restrictions-android.md#kiosk) e [Windows 10](kiosk-settings.md) .

## <a name="see-also"></a>Consulte também

[Configurando e Solucionando problemas de dispositivos Android Enterprise no Microsoft Intune](https://support.microsoft.com/help/4476974)
