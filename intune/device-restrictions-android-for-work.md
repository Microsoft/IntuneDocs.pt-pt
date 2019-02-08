---
title: Definições de dispositivos empresariais Android no Microsoft Intune – Azure | Documentos da Microsoft
description: No Android Enterprise ou de dispositivos Android for Work, restringir as definições no dispositivo, incluindo copiar e colar, Mostrar notificações, permissões de aplicações, partilha de dados, comprimento de palavra-passe, falhas de início de sessão, utilize a impressão digital para desbloquear, reutilização de palavras-passe e ativar o bluetooth partilha de contactos profissionais. Configure dispositivos como um quiosque para executar uma aplicação ou várias aplicações.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e79572b6815f2aded8f3145969beac4233e415b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844229"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos do Android Enterprise para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve as diferentes definições que pode controlar em dispositivos Android Enterprise. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, execução de aplicações no modo de local público, controlo de segurança e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Proprietário do dispositivo apenas

### <a name="general-settings"></a>Definições gerais

- **Captura de ecrã**: Escolher **bloco** impedir capturas de ecrã ou tela captura no dispositivo. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite ao utilizador capturar o conteúdo do ecrã como uma imagem.
- **Câmara**: Escolher **bloco** para impedir o acesso à câmara do dispositivo. **Não é necessário** permite o acesso à câmara do dispositivo.
- **Política de permissão predefinida**: Esta definição define a política de permissão predefinida para pedidos de permissões de runtime. Os valores possíveis incluem:
  - **Predefinição do dispositivo**: Utilize predefinição do dispositivo.
  - **Linha de comandos**: É pedido ao utilizador para aprovar a permissão.
  - **Conceder automaticamente**: Permissões são concedidas automaticamente.
  - **Negar automaticamente**: As permissões são rejeitadas automaticamente.
- **Alterações de data e hora**: Escolher **bloco** para impedir que os utilizadores, desde a configuração manualmente a data e hora. **Não configurado** permite aos utilizadores para a data definida e a hora no dispositivo.
- **Alterações de volume**: Escolher **bloco** para impedir que os utilizadores alterem o volume do dispositivo. **Não configurado** permite utilizando as definições de volume no dispositivo.
- **Reposição de fábrica**: Escolher **bloco** para impedir que os utilizadores com o factory reposição opção nas definições do dispositivo. **Não configurado** permite aos utilizadores utilizar esta definição no dispositivo.
- **Arranque seguro**: Escolher **bloco** para impedir que os utilizadores reiniciar o dispositivo em modo de segurança. **Não configurado** permite aos utilizadores reiniciar o dispositivo em modo de segurança.
- **Barra de status**: Escolher **bloco** para impedir o acesso a barra de estado, incluindo notificações e definições rápidas. **Não configurado** permite aos utilizadores acesso a barra de status.
- **Serviços de dados de roaming**: Escolher **bloco** para impedir que os dados em roaming na rede celular. **Não configurado** permite dados em roaming quando o dispositivo estiver numa rede celular.
- **As alterações de definições de Wi-Fi**: Escolher **bloco** para impedir que os utilizadores alterem as definições de Wi-Fi criadas pelo proprietário do dispositivo. Os utilizadores podem criar suas próprias configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração de ponto de acesso Wi-Fi**: Escolher **bloco** para impedir que os utilizadores a criar ou alterar quaisquer configurações de Wi-Fi. **Não configurado** permite que os usuários alterar as definições de Wi-Fi no dispositivo.
- **Configuração de Bluetooth**: Escolher **bloco** para impedir que os utilizadores configurem Bluetooth no dispositivo. **Não configurado** permite o uso de Bluetooth no dispositivo.
- **Tethering e acesso a pontos ativos**: Escolher **bloco** para impedir que tethering e acesso a pontos ativos portátil. **Não configurado** permite tethering e acesso a pontos ativos portátil.
- **Armazenamento USB**: Escolher **permitir** para o armazenamento USB de acesso no dispositivo. **Não configurado** impede o acesso a armazenamento USB.
- **Transferência de ficheiros USB**: Escolher **bloco** para impedir a transferência de ficheiros através de USB. **Não configurado** permite a transferência de ficheiros.
- **Suporte de dados externo**: Escolher **bloco** para impedir a utilizar ou ligar a qualquer suporte de dados externo no dispositivo. **Não configurado** permite o suporte de dados externo no dispositivo.
- **Feixe dados através de NFC**: Escolher **bloco** para impedir a utilização da tecnologia de junto ao campo comunicação (NFC) a feixe dados a partir de aplicações. **Não configurado** permite o uso de NFC para partilhar dados entre dispositivos.
- **Recursos de depuração**: Escolher **permitir** para permitir que os utilizadores utilizem os recursos de depuração no dispositivo. **Não configurado** impede que os usuários usando os recursos de depuração no dispositivo.
- **Ajuste do microfone**: Escolher **bloco** para impedir que os utilizadores de ativação do som do microfone e ajustar o volume do microfone. **Não configurado** permite ao utilizador utilizar e ajustar o volume do microfone do dispositivo.
- **E-mails de proteção de reposição de fábrica**: Escolher **endereços de e-mail de conta Google**. Introduza os endereços de e-mail dos administradores de dispositivos que possam desbloquear o dispositivo depois de serem eliminado. Certifique-se de que separe os endereços de e-mail com ponto e vírgula, por exemplo, `admin1@gmail.com;admin2@gmail.com`. Se uma mensagem de e-mail não é inserida, qualquer pessoa pode desbloquear o dispositivo após o restauro para as definições de fábrica.
- **Saída de emergência da rede**: Escolher **ativar** para permitir que os utilizadores ativar a funcionalidade de Sombreado traçado de escape de rede. Se uma conexão de rede não é feita quando o dispositivo for arrancado, a saída de emergência pede para temporariamente ligar a uma rede e atualizar a política de dispositivo. Depois da aplicação da política, a rede temporária é esquecida e o dispositivo continua o arranque. Esta funcionalidade liga dispositivos a uma rede se:
  - Não existe uma rede adequada na política de última.
  - O dispositivo for arrancado numa aplicação no modo de bloqueio de tarefa.
  - O utilizador é não é possível alcançar as definições do dispositivo.

  **Não configurado** impede que os utilizadores de ativarem a funcionalidade de Sombreado traçado de escape de rede no dispositivo.

- **Permitir a instalação de origens desconhecidas**: Escolher **permitir** para que os utilizadores podem ativar o **origens desconhecidas**. Esta definição permite que as aplicações instalar a partir de origens desconhecidas. **Não configurado** impede que os utilizadores de ativarem **origens desconhecidas**.
- **Atualização do sistema**: Escolha uma opção para definir a forma como o dispositivo processa atualizações por ondas eletromagnéticas:
  - **Predefinição do dispositivo**: Utilize predefinição do dispositivo.
  - **Automática**: As atualizações são instaladas automaticamente sem interação do utilizador. Definir esta política imediatamente instala todas as atualizações pendentes.
  - **Adiado**: As atualizações são adiadas durante 30 dias. No final dos 30 dias, o Android solicita ao utilizador para instalar a atualização. É possível os fabricantes de dispositivos ou operadoras impedirem (isentarem) o adiamento de atualizações de segurança importantes. Uma atualização isenta mostra uma notificação de sistema ao utilizador no dispositivo. 
  - **Janela de manutenção**: Instala atualizações automaticamente durante uma janela de manutenção diária que definir no Intune. Instalação tenta diariamente durante 30 dias e pode falhar se houver níveis insuficientes de espaço ou útil da bateria. Após 30 dias, o Android solicita ao utilizador que instalar. Esta janela também é utilizada para instalar atualizações para aplicações do Play. Utilize esta opção para dispositivos dedicados, tais como quiosques, como aplicações de primeiro plano de local público de aplicação única podem ser atualizadas.
- **É atualizado automaticamente a aplicação**: Escolha quando são instaladas as atualizações automáticas. As opções são:
  - **Não configurado**
  - **Preferência de utilizador**
  - **Nunca**
  - **Apenas Wi-Fi**
  - **Sempre**

- **Windows de notificação**: Quando definido como **desativar**, notificações de janela, incluindo circula, as chamadas recebidas, as chamadas, alertas de sistema e erros de sistema não são apresentadas no dispositivo. Quando definido como **não configurado**, a predefinição do sistema operativo é usada, que pode ser para mostrar notificações.
- **Ignorar primeiro utilizar sugestões**: Escolher **ativar** para ocultar ou ignorar sugestões de aplicações para acompanhar tutoriais ou ler qualquer sugestão introdutório quando a aplicação for iniciada. Quando definido como **não configurado**, a predefinição do sistema operativo é usada, que pode ser para mostrar estas sugestões quando a aplicação for iniciada.


### <a name="system-security-settings"></a>Definições de segurança do sistema

- **Análise de ameaças nas aplicações**: **Exigir** impõe que o **verificar aplicações** definição está ativada para o trabalho e perfis pessoais.

### <a name="kiosk-settings"></a>Definições de quiosque

Pode configurar um dispositivo para executar uma aplicação ou muitas aplicações. Quando um dispositivo está no modo de local público, apenas as aplicações que adicionar estão disponíveis. Estas definições aplicam-se ao Android dispositivos dedicados, mas não para o Android totalmente gerido dispositivos dedicados.

**Modo de local público**: Escolha se o dispositivo será executado uma aplicação ou várias aplicações.

- **Quiosque de uma aplicação**: Os utilizadores só podem aceder uma única aplicação no dispositivo. Quando o dispositivo é iniciado, apenas a aplicação específica é iniciada. Os utilizadores não podem abrir novas aplicações ou mudar a aplicação em execução.

  **Passos**
  1. Escolher **Selecione uma aplicação gerida**e selecione a aplicação do Google Play gerida a partir da lista. 

      Se não tiver todas as aplicações listadas, em seguida, [adicionar algumas aplicações Android](apps-add-android-for-work.md) no dispositivo. Não se esqueça [atribuir a aplicação para o grupo de dispositivos que criou para os seus dispositivos de local público](apps-deploy.md).

  2. Escolher **OK** > **OK** para adicionar a aplicação.

- **Quiosque de várias aplicações**: Os utilizadores podem aceder um conjunto limitado de aplicações no dispositivo. Quando o dispositivo é iniciado, inicie apenas as aplicações que adicionar. Também pode adicionar alguns links da web que os utilizadores podem abrir. Quando a política é aplicada, os utilizadores veem ícones para aplicações permitidas na tela inicial.

  > [IMPORTANTE] Para dispositivos de local público de várias aplicações, o [aplicação gerida ecrãs home page](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) no Google Play **tem de ser**:
  >   - [Adicionado como uma aplicação de cliente](apps-add-android-for-work.md) no Intune
  >   - [Atribuído ao grupo de dispositivos](apps-deploy.md) criado para os seus dispositivos de local público
  > 
  > O **geridos tela home page** aplicação não é necessário para estar no perfil de configuração, mas é necessário para ser adicionado como uma aplicação de cliente. Quando o **geridos tela home page** aplicação é adicionada como uma aplicação de cliente, todas as outras aplicações que adiciona no perfil de configiration são apresentadas como ícones no o **geridos tela home page** aplicação. 

  - Escolher **adicionar**e selecione as suas aplicações na lista.

    Se o **geridos tela home page** aplicação não estiver listada, em seguida, [adicioná-lo a partir do Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Não se esqueça [atribuir a aplicação](apps-deploy.md) para o grupo de dispositivos que criou para os seus dispositivos de local público.

    Também pode adicionar outros [aplicações Android](apps-add-android-for-work.md) e [aplicações web](web-app.md) criados pela sua organização para o dispositivo. Não se esqueça [atribuir a aplicação para o grupo de dispositivos que criou para os seus dispositivos de local público](apps-deploy.md).

  - **Botão início virtual**: Escolher **ativar** para mostrar um botão de início do dispositivo de quiosque. Quando selecionado, o utilizador ele retorna ao ecrã principal do dispositivo para que os usuários podem alternar facilmente entre aplicações. Em alguns dispositivos Android, que os usuários precisem percorra a cópia de segurança no ecrã para mostrar o botão de início. **Desativar** não mostra um botão de início, para que os utilizadores podem utilizar o botão de retrocesso para alternar entre aplicações.
  - **Saia do modo de local público**: Escolher **ativar** para permitir aos administradores interromper temporariamente o modo de local público para atualizar o dispositivo. Para utilizar esta funcionalidade, o administrador efetua o seguinte: 
  
    1. Continue selecionar o botão voltar, até que o botão de "Saída quiosque" é mostrado. 
    2. Selecione o botão e introduza o **deixar o código do modo de local público** PIN.
    3. Quando terminar de efetuar alterações, selecione o **geridos tela home page** aplicação. Este passo relocks o dispositivo em modo de local público de várias aplicações. 
    
    **Desativar** não dá a capacidade de colocar em pausa o modo de local público. Se o administrador continua selecionar o botão voltar e seleciona o botão "Quiosque de saída", em seguida, uma mensagem indica que um código de acesso é necessário.
    
    - **Deixe o código do modo de local público**: Introduza um dígito de 4 a 6 PIN numérico. O administrador utiliza este PIN para interromper temporariamente o modo de local público.
 
  - **Definir o fundo de URL personalizado**: Introduza um URL para personalizar o ecrã de segundo plano no dispositivo local público.

### <a name="device-password-settings"></a>Definições de palavra-passe do dispositivo

- **Keyguard**: Escolher **desativar** para impedir que utiliza a utilizar a funcionalidade de ecrã de bloqueio de Keyguard no dispositivo. **Não configurado** permite que o usuário a usar os recursos de Keyguard.
- **Desativado as funcionalidades de keyguard**: Quando keyguard está ativada no dispositivo, escolha quais as funcionalidades para desativar. Por exemplo, quando **câmara segura** estiver marcada, a funcionalidade de câmera está desativada no dispositivo. Quaisquer funcionalidades não verificadas estão ativadas no dispositivo.
- **Tipo de palavra-passe obrigatório**: Defina o tipo de palavra-passe necessária para o dispositivo. As opções são:
  - **Pelo menos numérica**
  - **Complexo numérico**: Repetido ou números consecutivos, como "1111" ou "1234", não são permitidos.
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Comprimento mínimo da palavra-passe**: Introduza o comprimento mínimo da palavra-passe de que um utilizador tem de introduzir (entre 4 e 16 carateres).
- **Número de falhas de início de sessão antes de limpar o dispositivo**: Introduza o número de inícios de sessão falhados a permitir antes do dispositivo ser apagado (entre 1 a 11).

### <a name="power-settings"></a>Definições de energia

- **Tempo para o ecrã de bloqueio**: Defina o período de tempo em inatividade necessário antes do bloqueio do dispositivo.
- **Ecrã ligado enquanto o dispositivo ligado**: Escolha a que origens de dados com que o ecrã do dispositivo para se manter quando ligado.

### <a name="users-and-accounts-settings"></a>Definições de utilizadores e contas

- **Adicionar novos utilizadores**: Escolher **bloco** impedir os utilizadores de adicionar novos utilizadores. Cada utilizador tem um espaço pessoal no dispositivo para personalizado Home ecrãs, contas, aplicações e definições. **Não configurado** permite aos utilizadores adicionar outros utilizadores no dispositivo.
- **Remoção do utilizador**: Escolher **bloco** impedir os utilizadores de remoção de utilizadores. **Não configurado** permite aos utilizadores remover outros utilizadores do dispositivo.
- **Alterações de conta**: Escolher **bloco** impedir os utilizadores de modificação de contas. **Não configurado** permite aos usuários atualizar as contas de utilizador no dispositivo.

### <a name="connectivity"></a>Conectividade

- **VPN sempre ativada**: Escolher **ativar** para definir um cliente VPN para se ligar e voltar a ligar à VPN automaticamente. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN Sempre Ativada num único dispositivo. Não é suportado implementar várias políticas de VPN Sempre Ativada num único dispositivo.

- **Cliente VPN**: Escolha um cliente VPN que suporte Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID do pacote**: Introduza o ID de pacote da aplicação na Google Play store. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  >  - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  >  - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolher **ativar** para forçar todo o tráfego de rede para utilizar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="work-profile-only"></a>Apenas perfil de trabalho 

### <a name="work-profile-settings"></a>Definições de perfil de trabalho

#### <a name="general"></a>Geral

- **Copiar e colar entre perfis pessoais e de trabalho**: Escolher **bloco** para impedir a copiar e colar entre aplicações pessoais e de trabalho. **Não configurado** permite aos utilizadores partilhar dados através de copiar e colar com aplicações no perfil pessoal 
- **Partilha de dados entre perfis pessoais e de trabalho**: Escolha se as aplicações no perfil de trabalho podem partilhar com aplicações no perfil pessoal. Por exemplo, pode controlar ações compartilhamento em aplicativos, como o **partilha...** na aplicação do browser Chrome. Esta definição não se aplica ao comportamento da área de transferência de copiar/colar. As opções de partilha:
  - **Restrições de partilha predefinidas**: O comportamento de partilha predefinido do dispositivo, que varia consoante a versão Android. Por predefinição, é permitida a partilha do perfil pessoal com o perfil de trabalho. Também por predefinição, é bloqueada a partilha do perfil de trabalho para o perfil pessoal. Esta definição impede a partilha de dados do perfil de trabalho para o perfil pessoal. Em dispositivos com a versão 6.0 e versões posteriores, a Google não bloqueia a partilha do perfil pessoal para o perfil de trabalho.
  - **As aplicações no perfil de trabalho podem processar o pedido de partilha do perfil pessoal**: Permite que a funcionalidade do Android incorporada que permite a partilha do perfil pessoal para o perfil de trabalho. Quando ativada, um pedido de partilha de uma aplicação no perfil pessoal pode partilhar com aplicações no perfil de trabalho. Esta definição é o comportamento predefinido para dispositivos Android com versões anteriores à 6.0.
  - **Permitir partilha entre limites**: Ativa a partilha entre limites do perfil de trabalho em ambas as direções. Quando seleciona esta definição, as aplicações no perfil de trabalho podem partilhar dados com aplicações sem destaque no perfil pessoal. Esta definição permite que aplicações geridas no perfil de trabalho partilhem com aplicações no lado não gerido do dispositivo. Por isso, utilize esta definição com cuidado.

- **Notificações do perfil de trabalho, enquanto o dispositivo está bloqueado**: Controla se a aplicações no perfil de trabalho podem mostrar dados em notificações quando o dispositivo está bloqueado. **Bloco** não mostra os dados. **Não configurado** mostra os dados.
- **Permissões de aplicações predefinidas**: Predefine a política de permissões para todas as aplicações do perfil de trabalho. A partir do Android 6, é pedido ao utilizador para conceder determinadas permissões necessárias pelas aplicações quando a aplicação é iniciada. Esta definição de política permite-lhe decidir se é pedido aos utilizadores a concessão de permissões para todas as aplicações no perfil de trabalho. Por exemplo, poderá atribuir uma aplicação ao perfil de trabalho que precisa de acesso de localização. Normalmente, essa aplicação pede ao utilizador para aprovar ou recusar o acesso à localização da aplicação. Utilize esta política para conceder permissões automaticamente sem aviso, recusar permissões automaticamente sem aviso ou permitir que o utilizador final decida. Escolha entre:
  - **Predefinição do dispositivo**
  - **Pedido de confirmação**
  - **Conceder automaticamente**
  - **Negar automaticamente**

  Também pode utilizar uma política de Configuração de Aplicações para conceder permissões a aplicações individuais (**Aplicações Cliente** > **Políticas de configuração da aplicação**).

- **Adicionar e remover contas**: Escolher **bloco** para impedir que os utilizadores finais de adicionarem ou removerem contas no perfil de trabalho manualmente. Por exemplo, ao implementar a aplicação Gmail num perfil de trabalho do Android, pode impedir os utilizadores finais de adicionarem ou removerem contas neste perfil de trabalho. **Não configurado** permite adicionar contas no perfil de trabalho.  

- **Partilha de contactos através de Bluetooth**: Permite aceder aos contactos de outro dispositivo, como um carro, que se encontra emparelhado com Bluetooth de trabalhar. Por predefinição, esta definição não está configurada e os contactos do perfil de trabalho não são apresentados. Selecione **Ativar** para permitir esta partilha e mostrar os contactos do perfil de trabalho. Esta definição aplica-se a dispositivos de perfil de trabalho do Android em Android OS v6.0 e mais recentes. Ativar esta definição pode permitir que determinados dispositivos Bluetooth coloquem os contactos de trabalho na cache após a primeira ligação. A desativação desta política após um emparelhamento/sincronização inicial pode não remover os contactos de trabalho dos dispositivos Bluetooth.

- **Captura de ecrã**: Escolher **bloco** impedir capturas de ecrã ou tela captura no dispositivo no perfil de trabalho. Também impede que os conteúdos presentes sejam apresentados em dispositivos de visualização que não tenham uma saída de vídeo segura. **Não configurado** permite obter capturas de ecrã.

- **Apresentar id contacto de trabalho autor da chamada no perfil pessoal**: Quando ativada (**não configurado**), os detalhes de contacto autor da chamada de trabalho são apresentados no perfil pessoal. Quando definido como **bloco**, o número de contacto autor da chamada do trabalho não for apresentado no perfil pessoal. Aplica-se ao Android OS v6.0 e a versões mais recentes.

- **Pesquisar contactos de trabalho do perfil pessoal**: Escolher **bloco** para impedir que os utilizadores a procurar contactos de trabalho nas aplicações no perfil pessoal. **Não é necessário** permite procurar contactos de trabalho no perfil pessoal.

- **Câmara**: Escolher **bloco** para impedir o acesso à câmara do dispositivo no perfil de trabalho. A câmara na parte pessoal não é afetada por esta definição. **Não é necessário** permite o acesso à câmara no perfil de trabalho.

#### <a name="work-profile-password"></a>Palavra-passe de perfil de trabalho

- **Exigir palavra-passe de perfil de trabalho**: Aplica-se ao Android 7.0 e superior com o perfil de trabalho ativado. Escolher **requerem** para introduzir uma política de código de acesso que aplica-se apenas às aplicações no perfil de trabalho. Por predefinição, o utilizador final pode utilizar os dois PINs definidos separadamente ou pode optar por combinar os PINs no mais forte dos dois. **Não configurado** permite ao utilizador utilizar aplicações de trabalho, sem introduzir uma palavra-passe.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de carateres de palavra-passe do utilizador tem de ter, partir **4**-**16**.
- **Máximo de minutos de inatividade até o trabalho ao bloqueio do perfil**: Selecione o período de tempo antes do perfil de trabalho ser bloqueado. Em seguida, o utilizador tem de introduzir as credenciais para recuperar o acesso.
- **Número de falhas de início de sessão antes de limpar o dispositivo**: Introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes do perfil de trabalho é eliminado do dispositivo.
- **Expiração de palavra-passe (dias)**: Introduza o número de dias até ser preciso alterar palavra-passe de um utilizador final (de **1**-**255**).
- **Tipo de palavra-passe obrigatório**: Selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: Não são permitidos números repetidos ou consecutivos, como "1111" ou "1234"
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de novas palavras-passe tem de ser utilizada antes de uma palavra-passe antiga pode ser reutilizada (de **1**-**24**).
- **Desbloqueio por impressão digital**: Escolher **bloco** e impedir que os utilizadores finais utilizem a impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite aos utilizadores desbloquear os dispositivos com uma impressão digital no perfil de trabalho.
- **Smart Lock e outros agentes de fidedignidade**: Escolher **bloco** para impedir que o Smart Lock ou outros agentes de fidedignidade de ajustarem as definições de ecrã de bloqueio em dispositivos compatíveis. Esta funcionalidade, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de ecrã do bloqueio de dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="device-password"></a>Palavra-passe do dispositivo

Estas definições de palavra-passe aplicam-se aos perfis pessoais nos dispositivos que utilizam um perfil de trabalho.

- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de carateres de palavra-passe do utilizador tem de ter, partir **4**-**14**.
- **Máximo de minutos de inatividade até o ecrã bloquear**: Selecione a quantidade de tempo antes de um dispositivo inativo ser automaticamente bloqueado
- **Número de falhas de início de sessão antes de limpar o dispositivo**: Introduza o número de vezes que uma palavra-passe incorreta pode ser introduzida antes de serem eliminados todos os dados do dispositivo
- **Expiração de palavra-passe (dias)**: Introduza o número de dias até ser preciso alterar palavra-passe de um utilizador final (de **1**-**255**)
- **Tipo de palavra-passe obrigatório**: Selecione o tipo de palavra-passe que tem de ser definido no dispositivo. Escolha entre:
  - **Predefinição do dispositivo**
  - **Biométrica de segurança baixa**
  - **Necessário**
  - **Pelo menos numérica**
  - **Complexo numérico**: Não são permitidos números repetidos ou consecutivos, como "1111" ou "1234"
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**
- **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de novas palavras-passe tem de ser utilizada antes de uma palavra-passe antiga pode ser reutilizada (de **1**-**24**).
- **Desbloqueio por impressão digital**: Escolher **bloco** para impedir que o utilizador final utilizar a impressão digital do dispositivo para desbloquear o dispositivo. **Não configurado** permite ao utilizador desbloquear o dispositivo através de uma impressão digital.
- **Smart Lock e outros agentes de fidedignidade**: Escolher **bloco** para impedir que o Smart Lock ou outros agentes de fidedignidade de ajustarem as definições de ecrã de bloqueio em dispositivos compatíveis. Esta funcionalidade, por vezes conhecida como agente de confiança, permite desativar ou ignorar a palavra-passe de ecrã do bloqueio de dispositivo se o dispositivo estiver numa localização fidedigna. Por exemplo, ignore a palavra-passe do perfil de trabalho quando o dispositivo está ligado a um dispositivo Bluetooth específico ou quando está próximo de uma etiqueta NFC. Utilize esta definição para impedir que os utilizadores configurem o Smart Lock.

### <a name="system-security"></a>Segurança do sistema

- **Análise de ameaças nas aplicações**: **Exigir** impõe que o **verificar aplicações** definição está ativada para o trabalho e perfis pessoais.

   > [!Note]
   > Esta definição só funciona para dispositivos Android O e posteriores.

### <a name="connectivity"></a>Conectividade

- **VPN sempre ativada**: Escolher **ativar** para definir um cliente VPN para se ligar e voltar a ligar à VPN automaticamente. As ligações VPN Sempre Ativada permanecem ativadas ou ativam-se imediatamente quando o utilizador bloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. 

  Selecione **Não configurado** para desativar a VPN sempre ativada para todos os clientes VPN.

  > [!IMPORTANT]
  > Certifique-se de que implementa apenas uma política de VPN Sempre Ativada num único dispositivo. Não é suportado implementar várias políticas de VPN Sempre Ativada num único dispositivo.

- **Cliente VPN**: Escolha um cliente VPN que suporte Always On. As opções são:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizar
    - **ID do pacote**: Introduza o ID de pacote da aplicação na Google Play store. Por exemplo, se o URL da aplicação na Play Store for `https://play.google.com/store/details?id=com.contosovpn.android.prod`, o ID de pacote é `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - O cliente VPN que escolher tem de estar instalado no dispositivo e deve suportar a VPN por aplicação em perfis de trabalho. Caso contrário, será apresentado um erro. 
  >  - Tem de aprovar a aplicação cliente VPN na **Managed Google Play Store**, sincronizar a aplicação com o Intune e implementar a aplicação no dispositivo. Depois de o fazer, a aplicação é instalada no perfil de trabalho do utilizador.
  >  - Aqui pode ser problemas conhecidos ao utilizar a VPN por aplicação com acesso de F5 para Android 3.0.4. Ver [notas de versão da F5 para acesso de F5 para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android) para obter mais informações.

- **Modo de bloqueio**: Escolher **ativar** para forçar todo o tráfego de rede para utilizar o túnel VPN. Se não for estabelecida uma ligação à VPN, o dispositivo não terá acesso à rede.

  Selecione **Não configurado** para permitir que o tráfego flua através do túnel VPN ou através da rede móvel.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de local público para [Android](device-restrictions-android.md#kiosk) e [com o Windows 10](kiosk-settings.md) dispositivos.
