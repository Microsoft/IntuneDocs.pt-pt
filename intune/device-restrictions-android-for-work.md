---
title: Definições de dispositivos empresariais Android no Microsoft Intune – Azure | Documentos da Microsoft
description: No Android Enterprise ou de dispositivos Android for Work, restringir as definições no dispositivo, incluindo copiar e colar, Mostrar notificações, permissões de aplicações, partilha de dados, comprimento de palavra-passe, falhas de início de sessão, utilize a impressão digital para desbloquear, reutilização de palavras-passe e ativar o bluetooth partilha de contactos profissionais. Configure dispositivos como um quiosque de dispositivo dedicado para executar um aplicativo ou vários aplicativos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8bd537315a09c0c7cf338ac0892fc4ae3d1dc8fc
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550181"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos do Android Enterprise para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, executar aplicativos em dispositivos dedicados, controlar a segurança e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

### <a name="general-settings"></a>Definições gerais

- **Captura de ecrã**: escolha **Bloquear** para impedir as capturas de ecrã no dispositivo. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Câmara**: escolha **Bloquear** para impedir o acesso à câmara no dispositivo. **Não é necessário** permite o acesso à câmara do dispositivo.
- **Política de permissão padrão**: Essa configuração define a política de permissão padrão para solicitações de permissões de tempo de execução. Os valores possíveis incluem:
  - **Padrão do dispositivo**: Use a configuração padrão do dispositivo.
  - **Prompt**: O usuário é solicitado a aprovar a permissão.
  - **Concessão automática**: As permissões são concedidas automaticamente.
  - **Negação automática**: As permissões são negadas automaticamente.
- **Alterações de data e hora**: Escolha **Bloquear** para impedir que os usuários configurem manualmente a data e a hora. **Não configurado** permite aos utilizadores para a data definida e a hora no dispositivo.
- **Alterações de volume**: Escolha **Bloquear** para impedir que os usuários alterem o volume do dispositivo. **Não configurado** permite utilizando as definições de volume no dispositivo.
- **Redefinição de fábrica**: Escolha **Bloquear** para impedir que os usuários usem a opção de redefinição de fábrica nas configurações do dispositivo. **Não configurado** permite aos utilizadores utilizar esta definição no dispositivo.
- **Inicialização segura**: Escolha **Bloquear** para impedir que os usuários reiniciem o dispositivo no modo de segurança. **Não configurado** permite aos utilizadores reiniciar o dispositivo em modo de segurança.
- **Barra de status**: Escolha **Bloquear** para impedir o acesso à barra de status, incluindo notificações e configurações rápidas. **Não configurado** permite aos utilizadores acesso a barra de status.
- **Serviços de dados**de roaming: escolha **Bloquear** para impedir o roaming de dados na rede móvel. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **Alterações de configuração de Wi-Fi**: Escolha **Bloquear** para impedir que os usuários alterem as configurações de Wi-Fi criadas pelo proprietário do dispositivo. Os utilizadores podem criar suas próprias configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração do ponto de acesso Wi-Fi**: Escolha **Bloquear** para impedir que os usuários criem ou alterem configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração de Bluetooth**: Escolha **Bloquear** para impedir que os usuários configurem o Bluetooth no dispositivo. **Não configurado** permite o uso de Bluetooth no dispositivo.
- **Compartilhamento de Internet e acesso a hotspots**: Escolha **Bloquear** para impedir o compartilhamento de Internet e o acesso a hotspots portáteis. **Não configurado** permite tethering e acesso a pontos ativos portátil.
- **Armazenamento USB**: Escolha **permitir** para acessar o armazenamento USB no dispositivo. **Não configurado** impede o acesso a armazenamento USB.
- **Transferência de arquivo USB**: Escolha **Bloquear** para impedir a transferência de arquivos por USB. **Não configurado** permite a transferência de ficheiros.
- **Mídia externa**: Escolha **Bloquear** para impedir o uso ou a conexão de qualquer mídia externa no dispositivo. **Não configurado** permite o suporte de dados externo no dispositivo.
- **Transmitir dados usando NFC**: Escolha **Bloquear** para impedir o uso da tecnologia NFC (comunicação a curta distância) para transmitir dados de aplicativos. **Não configurado** permite o uso de NFC para partilhar dados entre dispositivos.
- **Recursos de depuração**: Escolha **permitir** para permitir que os usuários usem recursos de depuração no dispositivo. **Não configurado** impede que os usuários usando os recursos de depuração no dispositivo.
- **Ajuste do microfone**: Escolha **Bloquear** para impedir que os usuários desmudom o microfone e ajuste o volume do microfone. **Não configurado** permite ao utilizador utilizar e ajustar o volume do microfone do dispositivo.
- **Emails de proteção**de redefinição de fábrica: Escolha **endereços de email da conta do Google**. Introduza os endereços de e-mail dos administradores de dispositivos que possam desbloquear o dispositivo depois de serem eliminado. Certifique-se de que separe os endereços de e-mail com ponto e vírgula, por exemplo, `admin1@gmail.com;admin2@gmail.com`. Se uma mensagem de e-mail não é inserida, qualquer pessoa pode desbloquear o dispositivo após o restauro para as definições de fábrica. Esses emails se aplicam somente quando uma redefinição de fábrica que não é de usuário é executada, como executar uma redefinição de fábrica usando o menu de recuperação.
- **Hachura de escape de rede**: Escolha **habilitar** para permitir que os usuários ativem o recurso de hachura de escape de rede. Se uma conexão de rede não é feita quando o dispositivo for arrancado, a saída de emergência pede para temporariamente ligar a uma rede e atualizar a política de dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Esta funcionalidade liga dispositivos a uma rede se:
  - Não existe uma rede adequada na política de última.
  - O dispositivo for arrancado numa aplicação no modo de bloqueio de tarefa.
  - O utilizador é não é possível alcançar as definições do dispositivo.

  **Não configurado** impede que os utilizadores de ativarem a funcionalidade de Sombreado traçado de escape de rede no dispositivo.

- **Atualização do sistema**: Escolha uma opção para definir como o dispositivo lida com as atualizações ao longo do ar:
  - **Padrão do dispositivo**: Use a configuração padrão do dispositivo.
  - **Automático**: As atualizações são instaladas automaticamente sem interação do usuário. Definir esta política imediatamente instala todas as atualizações pendentes.
  - **Adiado**: As atualizações são adiadas por 30 dias. No final dos 30 dias, o Android solicita ao utilizador para instalar a atualização. É possível os fabricantes de dispositivos ou operadoras impedirem (isentarem) o adiamento de atualizações de segurança importantes. Uma atualização isenta mostra uma notificação de sistema ao utilizador no dispositivo. 
  - **Janela de manutenção**: Instala atualizações automaticamente durante uma janela de manutenção diária que você define no Intune. Instalação tenta diariamente durante 30 dias e pode falhar se houver níveis insuficientes de espaço ou útil da bateria. Após 30 dias, o Android solicita ao utilizador que instalar. Esta janela também é utilizada para instalar atualizações para aplicações do Play. Use essa opção para dispositivos dedicados, como quiosques, como aplicativos de primeiro plano de dispositivo dedicado de aplicativo único podem ser atualizados.

- **Janelas de notificação**: Quando definido como **desabilitado**, as notificações de janela, incluindo solicitações de notificação, chamadas de entrada, chamadas de saída, alertas do sistema e erros do sistema não são mostradas no dispositivo. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode ser Mostrar notificações.
- **Ignorar primeiro dicas de uso**: Escolha **habilitar** para ocultar ou ignorar sugestões de aplicativos para percorrer tutoriais ou ler dicas introdutórias quando o aplicativo for iniciado. Quando definido como **não configurado**, o padrão do sistema operacional é usado, o que pode ser mostrar essas sugestões quando o aplicativo é iniciado.

### <a name="system-security-settings"></a>Definições de segurança do sistema

- **Análise de ameaças nas aplicações**: **Exigir** (padrão) habilita Google Play proteger para verificar aplicativos antes e depois que eles são instalados. Se detectar uma ameaça, ele poderá avisar o usuário para remover o aplicativo do dispositivo. **Não configurado** não habilita nem executa Google Play proteger para verificar aplicativos.

### <a name="dedicated-device-settings"></a>Configurações de dispositivo dedicado

Use essas configurações para configurar uma experiência em estilo de quiosque em seus dispositivos dedicados. Você pode configurar um dispositivo para executar um aplicativo ou executar muitos aplicativos. Quando um dispositivo é definido com o modo de quiosque, somente os aplicativos que você adiciona estão disponíveis. Essas configurações se aplicam a dispositivos Android Enterprise dedicados. Eles não se aplicam a dispositivos Android Enterprise totalmente gerenciados.

**Modo de quiosque**: Escolha se o dispositivo executa um aplicativo ou executa vários aplicativos.

- **Aplicativo único**: Os usuários só podem acessar um único aplicativo no dispositivo. Quando o dispositivo é iniciado, apenas a aplicação específica é iniciada. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

  - **Selecione um aplicativo gerenciado**: Selecione o aplicativo Google Play gerenciado na lista.

    Se não tiver todas as aplicações listadas, em seguida, [adicionar algumas aplicações Android](apps-add-android-for-work.md) no dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](apps-deploy.md).

  > [!IMPORTANT]
  > Ao usar o modo de quiosque de aplicativo único, os aplicativos de discagem/telefone podem não funcionar corretamente. 
  
- **Vários aplicativos**: Os usuários podem acessar um conjunto limitado de aplicativos no dispositivo. Quando o dispositivo é iniciado, inicie apenas as aplicações que adicionar. Também pode adicionar alguns links da web que os utilizadores podem abrir. Quando a política é aplicada, os utilizadores veem ícones para aplicações permitidas na tela inicial.

  > [!IMPORTANT]
  > Para dispositivos dedicados de vários aplicativos, o [aplicativo de tela inicial gerenciado](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) da Google Play **deve ser**:
  >   - [Adicionado como uma aplicação de cliente](apps-add-android-for-work.md) no Intune
  >   - [Atribuído ao grupo de dispositivos](apps-deploy.md) criado para seus dispositivos dedicados
  > 
  > O **geridos tela home page** aplicação não é necessário para estar no perfil de configuração, mas é necessário para ser adicionado como uma aplicação de cliente. Quando o aplicativo da **tela inicial gerenciada** é adicionado como um aplicativo cliente, todos os outros aplicativos adicionados no perfil de configuração são mostrados como ícones no aplicativo de **tela inicial gerenciado** . 
  >
  > Ao usar o modo de quiosque de vários aplicativos, os aplicativos de discagem/telefone podem não funcionar corretamente. 

  - **Adicionar**: Selecione seus aplicativos na lista.

    Se o **geridos tela home page** aplicação não estiver listada, em seguida, [adicioná-lo a partir do Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Certifique-se de [atribuir o aplicativo](apps-deploy.md) ao grupo de dispositivos criado para seus dispositivos dedicados.

    Também pode adicionar outros [aplicações Android](apps-add-android-for-work.md) e [aplicações web](web-app.md) criados pela sua organização para o dispositivo. Certifique-se de [atribuir o aplicativo ao grupo de dispositivos criado para seus dispositivos dedicados](apps-deploy.md).

  - **Botão Home virtual**: Um botão de chave flexível que retorna os usuários para a tela inicial gerenciada para que os usuários possam alternar entre aplicativos. As opções são:

    - **Não configurado** (predefinição): Um botão página inicial não é mostrado. Os usuários devem usar o botão voltar para alternar entre aplicativos.
    - **Passe o dedo para cima**: Um botão página inicial mostra quando um usuário passa o dedo para cima no dispositivo.
    - **Flutuante**: Mostra um botão Home persistente e flutuante no dispositivo.

  - **Sair do modo de quiosque**: Escolha **habilitar** para permitir que os administradores pausem temporariamente o modo de quiosque para atualizar o dispositivo. Para usar esse recurso, o administrador:
  
    1. Continua selecionando o botão voltar até que o botão **sair do quiosque** seja mostrado. 
    2. Seleciona o botão **sair do quiosque** e entra no **código do modo de quiosque** de saída.
    3. Quando terminar, selecione o aplicativo de **tela inicial gerenciado** . Este passo relocks o dispositivo em modo de local público de várias aplicações.

      Quando definido como **não configurado**, os administradores não podem pausar o modo de quiosque. Se o administrador continuar selecionando o botão voltar e seleciona o botão **sair do quiosque** , uma mensagem informa que uma senha é necessária.

    - **Deixe o código do modo de quiosque**: Insira um PIN numérico de 4-6 dígitos. O administrador utiliza este PIN para interromper temporariamente o modo de local público.

  - **Definir o plano de fundo da URL personalizada**: Insira uma URL para personalizar a tela de fundo no dispositivo dedicado.

    > [!NOTE]
    > Na maioria dos casos, é recomendável iniciar com imagens de pelo menos os seguintes tamanhos:
    >
    > - Telemóvel 1080x1920 px
    > - PC 1920 x 1080 px
    >
    > Para obter a melhor experiência e os detalhes nítidos, é recomendável que os ativos por imagem do dispositivo sejam criados para as especificações de exibição.
    >
    > Os monitores modernos têm densidades de pixel mais altas e podem exibir imagens de definição de 2K/4K equivalentes.

  - **Configuração de Wi-Fi**: **Habilitar** mostra o controle Wi-Fi na tela inicial gerenciada e permite que os usuários finais conectem o dispositivo a redes wifi diferentes. Habilitar esse recurso também ativa o local do dispositivo. **Não configurado** (padrão) não mostra o controle Wi-Fi na tela inicial gerenciada. Ele impede que os usuários se conectem a redes Wi-Fi usando a tela inicial gerenciada.

  - **Configuração de Bluetooth**: **Habilitar** mostra o controle Bluetooth na tela inicial gerenciada e permite que os usuários finais Emparelhem dispositivos via Bluetooth. Habilitar esse recurso também ativa o local do dispositivo. **Não configurado** (padrão) não mostra o controle Bluetooth na tela inicial gerenciada. Ele impede que os usuários configurem dispositivos Bluetooth e de emparelhamento ao usar a tela inicial gerenciada.

  - **Acesso à lanterna**: **Habilitar** mostra o controle de lanterna na tela inicial gerenciada e permite que os usuários finais ativem ou desativem a lanterna. **Não configurado** (padrão) não mostra o controle lanterna na tela inicial gerenciada. Ele impede que os usuários usem a lanterna ao usar a tela inicial gerenciada.

  - **Controle de volume de mídia**: **Habilitar** mostra o controle de volume de mídia na tela inicial gerenciada e permite que os usuários finais ajustem o volume de mídia do dispositivo usando um controle deslizante. **Não configurado** (padrão) não mostra o controle de volume de mídia na tela inicial gerenciada. Ele impede que os usuários ajustem o volume de mídia do dispositivo ao usar a tela inicial gerenciada, a menos que seus botões de hardware ofereçam suporte a ele. 

  - **Modo de proteção de tela**: **Habilitar** mostra uma barra de proteção na tela inicial gerenciada quando o dispositivo está bloqueado ou atinge o tempo limite. **Não configurado** (padrão) não mostra uma barra de proteção na tela inicial gerenciada.

    Quando habilitado, configure também:

    - **Definir imagem de proteção de tela personalizada**: Insira a URL para uma imagem personalizada. Por exemplo, digite:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Se você não inserir uma URL, a imagem padrão do dispositivo será usada, se houver uma imagem padrão.

    - **Número de segundos que o dispositivo mostra a proteção de tela antes**de desligar a tela: Escolha por quanto tempo o dispositivo mostra a proteção de tela. Insira um valor entre 0-9999999 segundos. O padrão `0` é segundos. Quando deixado em branco ou definido como zero (`0`), a proteção de tela estará ativa até que um usuário interaja com o dispositivo.
    - **Número de segundos em que o dispositivo fica inativo antes de mostrar a proteção de tela**: Escolha por quanto tempo o dispositivo ficará ocioso antes de mostrar a proteção de tela. Insira um valor entre 1-9999999 segundos. O padrão `30` é segundos. Você deve inserir um número maior que zero (`0`).
    - **Detectar mídia antes de iniciar a proteção de tela**: **Habilitar** (padrão) não mostrará a proteção de tela se áudio ou vídeo estiver sendo reproduzido no dispositivo. **Não configurado** mostra a proteção de tela, mesmo se o áudio ou vídeo estiver sendo reproduzido.

### <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Desabilitar tela de bloqueio**: Escolha **desabilitar** para impedir que os usuários usem o recurso de tela de bloqueio do keyguard no dispositivo. **Não configurado** permite que o usuário a usar os recursos de Keyguard.
- **Recursos da tela de bloqueio desabilitados**: Quando o keyguard estiver habilitado no dispositivo, escolha quais recursos serão desabilitados. Por exemplo, quando a **câmera segura** está marcada, o recurso de câmera é desabilitado no dispositivo. Todos os recursos não verificados estão habilitados no dispositivo.

  Esses recursos estão disponíveis para os usuários quando o dispositivo está bloqueado. Os usuários não verão nem acessarão os recursos que estão marcados.

- **Tipo obrigatório de palavra-passe**: Defina o tipo de senha necessário para o dispositivo. As opções são:
  - **Predefinição do dispositivo**
  - **Palavra-passe obrigatória, sem restrições**
  - **Biometria fraca**: veja [Strong vs. weak biometrics](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (Biometria forte versus fraca) (abre o site do Android)
  - **Numérica**: a palavra-passe só pode ter números, como `123456789`. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Complexo numérico**: não são permitidos números repetidos ou consecutivos, como “1111” ou “1234”. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfabética**: são obrigatórias letras do alfabeto. Não são obrigatórios números nem símbolos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérica**: inclui letras maiúsculas, letras minúsculas e carateres numéricos. Introduza o **comprimento mínimo da palavra-passe** que um utilizador tem de introduzir, entre 4 e 16 carateres.
  - **Alfanumérica com símbolos**: inclui letras maiúsculas, letras minúsculas, carateres numéricos, sinais de pontuação e símbolos. Introduza também:

    - **Comprimento mínimo da palavra-passe**: introduza o comprimento mínimo da palavra-passe, entre 4 e 16 carateres.
    - **Número de carateres obrigatórios**: introduza o número de carateres que a palavra-passe deverá ter, entre 0 e 16 carateres.
    - **Número de carateres em minúsculas obrigatórios**: introduza o número de carateres em minúsculas que a palavra-passe deverá ter, entre 0 e 16 carateres.
    - **Número de carateres em maiúsculas obrigatórios**: introduza o número de carateres em maiúsculas que a palavra-passe deverá ter, entre 0 e 16 carateres.
    - **Número de carateres não alfabéticos obrigatórios**: introduza o número de carateres não alfabéticos (tudo o que não seja letras do alfabeto) que a palavra-passe deverá ter, entre 0 e 16 carateres.
    - **Número de carateres numéricos obrigatórios**: introduza o número de carateres numéricos (`1`, `2`, `3` e assim por diante) que a palavra-passe deverá ter, entre 0 e 16 carateres.
    - **Número de carateres de símbolos obrigatórios**: introduza o número de carateres de símbolos (`&`, `#`, `%` e assim por diante) que a palavra-passe deverá ter, entre 0 e 16 carateres.

- **Número de dias até expirar a palavra-passe**: introduza o número de dias, entre 1 e 365, antes de ser necessário alterar a palavra-passe do dispositivo. Por exemplo, para alterar a palavra-passe após 60 dias, introduza `60`. Quando a palavra-passe expirar, será pedido aos utilizadores para criar uma nova.
- **Número de senhas necessárias antes que o usuário possa resuse uma senha**: introduza o número de palavras-passe recentes que não podem ser reutilizadas, entre 1 e 24. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.
- **Número de falhas de início de sessão antes de apagar o dispositivo**: Insira o número, entre 4-11, de entradas com falha para permitir antes que o dispositivo seja apagado.

### <a name="power-settings"></a>Definições de energia

- **Tempo para bloquear a tela**: Defina a quantidade de tempo ocioso necessária antes do bloqueio do dispositivo.
- **Tela enquanto o dispositivo estiver conectado**: Escolha quais fontes de energia fazem com que a tela do dispositivo permaneça ligada quando conectado.

### <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos usuários**: Escolha **Bloquear** para impedir que os usuários adicionem novos usuários. Cada utilizador tem um espaço pessoal no dispositivo para personalizado Home ecrãs, contas, aplicações e definições. **Não configurado** permite aos utilizadores adicionar outros utilizadores no dispositivo.
- **Remoção de usuário**: Escolha **Bloquear** para impedir que os usuários removam usuários. **Não configurado** permite aos utilizadores remover outros utilizadores do dispositivo.
- **Alterações de conta**: Escolha **Bloquear** para impedir que os usuários modifiquem contas. **Não configurado** permite aos usuários atualizar as contas de utilizador no dispositivo.

### <a name="applications"></a>Aplicações

- **Permitir a instalação de fontes**desconhecidas: Escolha **permitir** para que os usuários possam ativar **fontes**desconhecidas. Essa configuração permite que os aplicativos instalem de fontes desconhecidas, incluindo fontes diferentes da Google Play Store. **Não configurado** impede que os utilizadores de ativarem **origens desconhecidas**.
- **Permitir acesso a todos os aplicativos na Google Play Store**: Quando definido como **permitir**, os usuários obtêm acesso a todos os aplicativos na Google Play Store. Eles não obtêm acesso aos aplicativos que o administrador bloqueia em [aplicativos cliente](apps-add-android-for-work.md). **Não configurado** força os usuários a acessar apenas os aplicativos que o administrador disponibiliza Google Play armazenamento ou aplicativos necessários em [aplicativos cliente](apps-add-android-for-work.md).
- **Atualizações automáticas do aplicativo**: Escolha quando as atualizações automáticas estão instaladas. As opções são:
  - **Não configurado**
  - **Preferência de utilizador**
  - **Nunca**
  - **Apenas Wi-Fi**
  - **Sempre**

### <a name="connectivity"></a>Conectividade

- **VPN AlwaysOn**: Escolha **habilitar** para definir um cliente VPN para se conectar automaticamente e reconectar-se à VPN. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN Sempre Ativada num único dispositivo. Não é suportado implementar várias políticas de VPN Sempre Ativada num único dispositivo.

- **Cliente VPN**: Escolha um cliente VPN que ofereça suporte a Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID do pacote**: Insira a ID do pacote do aplicativo no repositório de Google Play. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  > - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="work-profile-only"></a>Apenas perfil de trabalho 

### <a name="work-profile-settings"></a>Definições de perfil de trabalho

#### <a name="general"></a>Geral

- **Copiar e colar entre perfis de trabalho e pessoais**: Escolha **Bloquear** para evitar copiar e colar entre aplicativos pessoais e de trabalho. **Não configurado** permite aos utilizadores partilhar dados através de copiar e colar com aplicações no perfil pessoal 
- **Compartilhamento de dados entre perfis pessoais e de trabalho**: Escolha se os aplicativos no perfil de trabalho podem compartilhar com aplicativos no perfil pessoal. Por exemplo, pode controlar ações compartilhamento em aplicativos, como o **partilha...** na aplicação do browser Chrome. Esta definição não se aplica ao comportamento da área de transferência de copiar/colar. As opções de partilha:
  - **Restrições de compartilhamento padrão**: O comportamento de compartilhamento padrão do dispositivo, que varia dependendo da versão do Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. Em dispositivos com a versão 6.0 e versões posteriores, a Google não bloqueia a partilha do perfil pessoal para o perfil de trabalho.
  - Os **aplicativos no perfil de trabalho podem lidar com a solicitação de compartilhamento do perfil pessoal**: Habilita o recurso interno do Android que permite o compartilhamento do perfil pessoal para trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Permitir o compartilhamento entre limites**: Permite o compartilhamento entre o limite do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Esta definição permite que aplicações geridas no perfil de trabalho partilhem com aplicações no lado não gerido do dispositivo. Por isso, utilize esta definição com cuidado.

- **Notificações de perfil de trabalho enquanto o dispositivo estiver bloqueado**: Controla se os aplicativos no perfil de trabalho podem mostrar dados em notificações quando o dispositivo está bloqueado. **Bloco** não mostra os dados. **Não configurado** mostra os dados.
- **Permissões de aplicativo padrão**: Predefine a política de permissões para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Utilize esta política para conceder permissões automaticamente sem aviso, recusar permissões automaticamente sem aviso ou permitir que o utilizador final decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

  Também pode utilizar uma política de Configuração de Aplicações para conceder permissões a aplicações individuais (**Aplicações Cliente** > **Políticas de configuração da aplicação**).

- **Adicionar e remover contas**: Escolha **Bloquear** para impedir que os usuários finais adicionem ou removam contas manualmente no perfil de trabalho. Por exemplo, ao implementar a aplicação Gmail num perfil de trabalho do Android, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho. **Não configurado** permite adicionar contas no perfil de trabalho.  

- **Compartilhamento de contatos via Bluetooth**: Habilita o acesso a contatos de trabalho de outro dispositivo, como um carro, que é emparelhado usando Bluetooth. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Ativar esta definição pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura de ecrã**: Escolha **Bloquear** para impedir capturas de tela ou capturas de telas no dispositivo no perfil de trabalho. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite obter capturas de ecrã.

- **Exibir ID do chamador do contato comercial no perfil pessoal**: Quando habilitado (**não configurado**), os detalhes do chamador de contato de trabalho são exibidos no perfil pessoal. Quando definido como **bloco**, o número de contacto autor da chamada do trabalho não for apresentado no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Pesquisar contatos de trabalho do perfil pessoal**: Escolha **Bloquear** para impedir que os usuários pesquisem contatos de trabalho em aplicativos no perfil pessoal. **Não é necessário** permite procurar contactos de trabalho no perfil pessoal.

- **Câmara**: Escolha **Bloquear** para impedir o acesso à câmera no dispositivo no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição. **Não é necessário** permite o acesso à câmara no perfil de trabalho.

#### <a name="work-profile-password"></a>Palavra-passe de perfil de trabalho

- **Exigir senha do perfil de trabalho**: Aplica-se ao Android 7,0 e superior com o perfil de trabalho habilitado. Escolher **requerem** para introduzir uma política de código de acesso que aplica-se apenas às aplicações no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois. **Não configurado** permite ao utilizador utilizar aplicações de trabalho, sem introduzir uma palavra-passe.
- **Comprimento mínimo da palavra-passe**: Insira o número mínimo de caracteres que a senha do usuário deve ter, de **4**-**16**.
- **Máximo de minutos de inatividade até o bloqueio do perfil de trabalho**: Selecione o período de tempo antes do bloqueio do perfil de trabalho. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de apagar o dispositivo**: Insira o número de vezes que uma senha incorreta pode ser inserida antes que o perfil de trabalho seja apagado do dispositivo.
- **Expiração da palavra-passe (dias)** : Insira o número de dias até que a senha de um usuário final deva ser alterada (de **1**-a**255**).
- **Tipo obrigatório de palavra-passe**: Selecione o tipo de senha que deve ser definida no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: Repetições ou números consecutivos, como ' 1111 ' ou ' 1234 ', não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: Insira o número de novas senhas que devem ser usadas antes que uma senha antiga possa ser reutilizada (de **1**-**24**).
- **Desbloqueio por impressão digital**: Escolha **Bloquear** para impedir que os usuários finais usem o scanner de impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite aos utilizadores desbloquear os dispositivos com uma impressão digital no perfil de trabalho.
- **Smart Lock e outros agentes de confiança**: Escolha **Bloquear** para impedir que Smart Lock ou outros agentes de confiança ajustem as configurações da tela de bloqueio em dispositivos compatíveis. Esta funcionalidade, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de ecrã do bloqueio de dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="device-password"></a>Palavra-passe do dispositivo

Estas definições de palavra-passe aplicam-se aos perfis pessoais nos dispositivos que utilizam um perfil de trabalho.

- **Comprimento mínimo da palavra-passe**: Insira o número mínimo de caracteres que a senha do usuário deve ter, de **4**-**14**.
- **Máximo de minutos de inatividade até o ecrã ser bloqueado**: Selecionar a quantidade de tempo antes que um dispositivo inativo seja bloqueado automaticamente
- **Número de falhas de início de sessão antes de apagar o dispositivo**: Insira o número de vezes que uma senha incorreta pode ser inserida antes que todos os dados sejam apagados do dispositivo
- **Expiração da palavra-passe (dias)** : Insira o número de dias até que a senha de um usuário final precise ser alterada (de **1**-a**255**)
- **Tipo obrigatório de palavra-passe**: Selecione o tipo de senha que deve ser definida no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: Repetições ou números consecutivos, como ' 1111 ' ou ' 1234 ', não são permitidos
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: Insira o número de novas senhas que devem ser usadas antes que uma senha antiga possa ser reutilizada (de **1**-**24**).
- **Desbloqueio por impressão digital**: Escolha **Bloquear** para impedir que o usuário final use o scanner de impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de confiança**: Escolha **Bloquear** para impedir que Smart Lock ou outros agentes de confiança ajustem as configurações da tela de bloqueio em dispositivos compatíveis. Esta funcionalidade, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de ecrã do bloqueio de dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="system-security"></a>Segurança do sistema

- **Análise de ameaças nas aplicações**: **Exigir** impõe que a configuração **verificar aplicativos** esteja habilitada para perfis pessoais e de trabalho.

   > [!Note]
   > Esta definição só funciona para dispositivos Android O e posteriores.

### <a name="connectivity"></a>Conectividade

- **VPN AlwaysOn**: Escolha **habilitar** para definir um cliente VPN para se conectar automaticamente e reconectar-se à VPN. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN Sempre Ativada num único dispositivo. Não é suportado implementar várias políticas de VPN Sempre Ativada num único dispositivo.

- **Cliente VPN**: Escolha um cliente VPN que ofereça suporte a Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID do pacote**: Insira a ID do pacote do aplicativo no repositório de Google Play. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  > - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  > - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolha **habilitar** para forçar todo o tráfego de rede a usar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de quiosque de dispositivo dedicados para dispositivos [Android](device-restrictions-android.md#kiosk) e [Windows 10](kiosk-settings.md) .

## <a name="see-also"></a>Consulte também

[Configurando e Solucionando problemas de dispositivos Android Enterprise no Microsoft Intune](https://support.microsoft.com/help/4476974)
