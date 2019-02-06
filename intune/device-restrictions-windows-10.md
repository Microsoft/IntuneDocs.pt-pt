---
title: Definições de restrição de dispositivos para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Ver uma lista de todas as definições e suas descrições para a criação de restrições de dispositivos no Windows 10 e dispositivos posteriores. Utilize estas definições no perfil de configuração para controlar as capturas de ecrã, requisitos de palavra-passe, definições de local público, aplicações na loja, Edge browser, defender do Windows, acesso para a cloud, o menu Iniciar e mais no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 6613b19102aac752e9717fc376d99a178fe9dd3c
ms.sourcegitcommit: ef85e28df802c974664305270c4a8571c0bb47b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742967"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos de 10 (e versões posteriores) do Windows para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve todas as configurações diferentes, que pode controlar no Windows 10 e dispositivos mais recentes. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, personalizar o ecrã de bloqueio, utilize o Windows Defender e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos seus dispositivos Windows 10.

> [!Note]
> Nem todas as opções estão disponíveis em todas as edições do Windows

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md).

## <a name="app-store"></a>App Store

- **Loja de aplicações (apenas móvel)**: Ative ou bloqueie a utilização da loja de aplicações em dispositivos Windows 10 Mobile.
- **Atualização automática de aplicações da loja**: Permite que aplicações instaladas a partir da Microsoft Store sejam atualizadas automaticamente.
- **Instalação de aplicação fidedigna**: Permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
- **Desbloqueio de programador**: Permitir que as definições de programador do Windows, como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.
- **Dados de aplicação do utilizador partilhados**: Permite que aplicações partilhem dados entre os diferentes utilizadores no mesmo dispositivo.
- **Utilizar apenas loja privada**: Ative para permitir apenas os utilizadores finais transferir aplicações da loja privada.
- **Lançamento de aplicação originado pela Store**: Utilizado para desativar todas as aplicações que foram previamente instaladas no dispositivo ou transferidas a partir da Microsoft Store.
- **Instalar dados da aplicação no volume do sistema**: Impede que as aplicações armazenem dados no volume do sistema do dispositivo.
- **Instalar aplicações na unidade do sistema**: Impede que as aplicações armazenem dados na unidade do sistema do dispositivo.
- **(Apenas ambiente de trabalho) de gravador de jogo**: Configura se é permitida a gravação e a difusão de jogos.
- **As aplicações da loja apenas**: Configura se os utilizadores podem instalar aplicações a partir de locais fora da loja de aplicações.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Canal de dados via rede móvel**: Impedir que os utilizadores de utilizar os dados, como navegação na web, quando estão ligados a uma rede celular. 
- **Roaming de dados**: Permitir roaming entre redes ao aceder a dados.
- **VPN na rede celular**: Controla se o dispositivo pode aceder a ligações VPN quando ligado a uma rede celular.
- **Roaming na rede celular de VPN**: Controla se o dispositivo pode aceder a ligações VPN quando está em roaming numa rede celular.
- **Bluetooth**: Controla se o utilizador pode ativar e configurar o Bluetooth no dispositivo.
- **Deteção de Bluetooth**: Permite que o dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
- **Pré-emparelhamento de Bluetooth**: Permite-lhe configurar dispositivos Bluetooth específicos para sejam emparelhados automaticamente com um dispositivo anfitrião.
- **Publicidade do Bluetooth**: Permite que os dispositivos recebam anúncios por Bluetooth.
- **Serviço de dispositivos ligados**: Permite-lhe escolher se pretende permitir que o serviço de dispositivos ligados, que permite a deteção e ligação a outros dispositivos Bluetooth.
- **NFC**: Permite que o utilizador ative e configure as funcionalidades junto ao campo comunicações (NFC) no dispositivo.
- **Wi-Fi**: Permite que o utilizador ative e configure Wi-Fi no dispositivo (apenas Windows 10 Mobile).
- **Ligar automaticamente a hotspots Wi-Fi**: Permite que o dispositivo ligue automaticamente a hotspots Wi-Fi gratuitos e aceite automaticamente os termos e condições para a ligação.
- **Configuração de Wi-Fi manual**: Controla se o utilizador pode configurar as suas próprias ligações Wi-Fi ou se este podem utilizar apenas ligações configuradas por um perfil de Wi-Fi (apenas Windows 10 Mobile).
- **Intervalo de deteção do Wi-Fi**: Especifique a frequência com que dispositivos verificar a existência de redes Wi-Fi. Especifique um valor de 1 (mais frequente) a 500 (menos frequente).
- **Serviços Bluetooth permitidos**: Especifica como cadeias de caracteres hexadecimais, uma lista de perfis e serviços Bluetooth permitidos.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Conta Microsoft**: Permite que o utilizador associe uma conta Microsoft ao dispositivo.
- **Conta não Microsoft**: Permite aos utilizadores adicionar contas de e-mail no dispositivo que não estão associados a uma conta Microsoft.
- **Sincronização de definições para a conta Microsoft**: Permitir que as definições de dispositivos e aplicações que estão associadas uma conta Microsoft sejam sincronizadas entre dispositivos.
- **Assistente de início de sessão Microsoft Account**: Escolher **desativar** para impedir que os utilizadores finais controla o serviço de Assistente de início de sessão no Microsoft (wlidsvc), como parar ou iniciar o serviço manualmente. Quando definido como **não configurado**, o serviço wlidsvc NT usa o padrão de sistema operativo (SO), que pode permitir que os utilizadores finais iniciar e parar o serviço. Este serviço é utilizado pelo sistema operacional para permitir aos utilizadores iniciar sessão respetiva conta Microsoft.

## <a name="cloud-printer"></a>Impressora em Cloud

- **URL de deteção de impressora**: Introduza o URL para localizar impressoras em cloud.
- **URL de autoridade de acesso de impressora**: Introduza o URL de ponto final de autenticação para obter os tokens de OAuth. Por exemplo, introduza algo como `https://login.microsoftonline.com/your Azure AD Tenant ID`.
- **GUID da aplicação de cliente nativo do Azure**: Introduza o GUID de um aplicativo de cliente é permitido obter OAuth tokens a partir de OAuthAuthority.
- **URI do recurso de serviço de impressão**: Introduza o URI do recurso OAuth para o serviço de impressão configurado no portal do Azure. Por exemplo, introduza algo como `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Impressoras máximas a consultar (apenas móvel)**: Introduza o número máximo de impressoras que deseja ser consultado. Por exemplo, introduza `10`.
- **O recurso de serviço de deteção de impressão URI**: Introduza o URI do recurso OAuth para a deteção de impressora serviço configurado no portal do Azure. Por exemplo, introduza algo como `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Depois de configurar o [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), pode configurar estas definições e, em seguida, implementar para dispositivos Windows.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Aplicação de definições**: Bloquear o acesso à aplicação de definições do Windows.
  - **Sistema**: Bloqueia o acesso à área do sistema da aplicação de definições.
    - **Modificação de definições de energia e suspensão (apenas ambiente de trabalho)**: Impede o utilizador final de alterar as definições de energia e suspensão no dispositivo.
  - **dispositivos**: Bloqueia o acesso à área de dispositivos da aplicação de definições.
  - **Rede de Internet**: Bloqueia o acesso à área de rede e internet da aplicação de definições.
  - **Personalização**: Bloqueia o acesso à área de personalização da aplicação de definições.
  - **Contas**: Bloqueia o acesso à área de contas da aplicação de definições.
  - **Hora e idioma**: Bloqueia o acesso à área de hora e idioma da aplicação de definições.
    - **Modificação da hora do sistema**: Impede o utilizador final de alterar a data e hora.
    - **Modificação das definições de região (apenas ambiente de trabalho)**: Impede o utilizador final de alterar as definições de região no dispositivo.
    - **Modificação de definições de idioma (apenas ambiente de trabalho)**: Impede que o utilizador alterar as definições de idioma no dispositivo.
  - **Jogos**: Bloqueia o acesso à aplicação jogos nas definições.
  - **Facilidade de acesso**: Bloqueia o acesso à facilidade de área de acesso da aplicação de definições.
  - **Privacidade**: Bloqueia o acesso à área de privacidade da aplicação de definições.
  - **Atualização e segurança**: Bloqueia o acesso à área de segurança da aplicação de definições e atualizações.

## <a name="display"></a>Apresentar

- **Ativar o dimensionamento da GDI para aplicações**
- **Desativar o dimensionamento da GDI para aplicações**

  Dimensionamento PPP de GDI permite que as aplicações que não são compatível com DPI para se tornar compatível com DPI por monitor. Introduza as aplicações legadas que tenham o dimensionamento PPP da GDI ativado. Com o dimensionamento PPP de GDI configurado para ativar e desativar uma aplicação, o dimensionamento é desativado para a aplicação.

## <a name="general"></a>Geral

- **(Apenas móvel) de captura de ecrã**: Permite ao utilizador capturar o ecrã do dispositivo como uma imagem.
- **Copiar e colar (apenas móvel)**: Permitir copiar e colar ações entre aplicações no dispositivo.
- **Anular inscrições manualmente**: Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
  - Esta definição de política não é aplicada se o computador estiver associado ao Azure AD e a inscrição automática estiver ativada. 
  - Esta definição de política não se aplica a computadores a executar o Windows 10 Home.
- **Instalação do certificado de raiz manual (apenas móvel)**: Impede o utilizador instalar manualmente certificados de raiz e os certificados CAP intermédios.

- **Câmara**: Permitir ou bloquear a utilização da câmara no dispositivo.
- **Sincronização de ficheiros do OneDrive**: Impede o dispositivo de sincronizar ficheiros no OneDrive.
- **Armazenamento amovível**: Especifica se os dispositivos de armazenamento externo, como cartões SD podem ser utilizados com o dispositivo.
- **Geolocalização**: Especifica se o dispositivo pode utilizar informações de serviços de localização.
- **Partilha da Internet**: Permite a utilização da partilha de ligação à Internet no dispositivo.
- **Reposição do telemóvel**: Controla se o utilizador pode fazer uma eliminação de dados no dispositivo.
- **Ligação USB (apenas móvel)**: Controla se os dispositivos podem aceder a dispositivos de armazenamento externo através de uma ligação USB.
- **Modo antiTheft (apenas móvel)**: Configurar se o modo Anti-roubo do Windows estiver ativado.
- **Cortana**: Ativar ou desativar o assistente de voz Cortana.
- **Gravação de voz (apenas móvel)**: Permitir ou bloquear a utilização do gravador de voz do dispositivo.
- **Modificação do nome do dispositivo**: Impede o utilizador final de alterar o nome do dispositivo (apenas Windows 10 Mobile)
- **Adicionar pacotes de aprovisionamento**: Bloqueia o agente de configuração de tempo de execução que instala os pacotes de aprovisionamento.
- **Remover pacotes de aprovisionamento**: Bloqueia o agente de configuração de tempo de execução que remove os pacotes de aprovisionamento.
- **Deteção de dispositivos**: Bloquear um dispositivo ser detetado por outros dispositivos.
- **(Apenas móvel) do comutador de tarefa**: Bloqueia o comutador de tarefas no dispositivo.
- **Caixa de diálogo de erro de cartão SIM (apenas móvel)**: Bloqueia uma mensagem de erro de ser apresentado no dispositivo se nenhum cartão SIM for detetado.
- **Área de trabalho de tinta**: Impedir que os utilizadores acedam a área de trabalho do ink. **Não configurado** folheio na área de trabalho de tinta e o utilizador tem permissão para usá-lo acima do ecrã de bloqueio.
- **Reimplementação automática**: Permite aos utilizadores com direitos administrativos eliminar todos os dados de utilizador e as configurações usando **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo é automaticamente reconfigurado e reinscrito na gestão.
- **Exigir que os utilizadores liguem à rede durante a configuração de dispositivo (apenas no Windows Insider)**: Escolher **requerem** para que o dispositivo estabelece ligação a uma rede antes de continuar após a página de rede durante a configuração do Windows 10. Enquanto esta funcionalidade estiver em pré-visualização, é necessário que tenha a versão 1809 ou versões posteriores do Windows Insider para utilizar esta definição.
- **Terminar a processos do Gerenciador de tarefas**: Esta definição determina se o não-administradores podem utilizar o Gestor de tarefas para tarefas de fim. **Bloco** impede que os usuários padrão (não-administradores) usando o Gerenciador de tarefas para terminar um processo ou tarefa no dispositivo. **Não configurado** (predefinição) permite que os usuários padrão encerrar um processo ou tarefa utilizando o Gestor de tarefas.

## <a name="kiosk-preview---obsolete"></a>Quiosque (Pré-visualização) – obsoleto

Estas definições são só de leitura e não podem ser alteradas. Para configurar o modo de quiosque, veja [Definições do Quiosque no Windows 10 e posterior](kiosk-settings.md).

Normalmente, um dispositivo de quiosque executa uma aplicação ou um conjunto específico de aplicações. Os utilizadores são impedidos de aceder a funcionalidades ou funções no dispositivo.

- **Modo de local público**: Identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

  - **Não configurado** (predefinição): A política não ativar o modo de local público no dispositivo.
  - **Quiosque de uma aplicação**: O perfil ativa o dispositivo execute apenas uma aplicação. Quando um utilizador inicia sessão, uma aplicação específica é iniciada. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
  - **Quiosque de várias aplicações**: O perfil ativa o dispositivo para executar muitos aplicativos. Apenas as aplicações que adicionar estão disponíveis para o utilizador. A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo, é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam e de remover as aplicações de que não precisam da respetiva vista.

#### <a name="single-app-kiosks"></a>Quiosques de uma aplicação

Introduza as seguintes definições:

- **Conta de utilizador**: Introduza a conta de utilizador local (para o dispositivo), uma conta de domínio do AD ou uma conta do Azure AD associado à aplicação de local público.
  - Conta local: Introduza como `devicename\accountname`, `.\accountname`, ou `accountname`
  - Conta de domínio: Introduza como `domain\accountname`
  - Conta do AD FS: Introduza como `AzureAD\emailaddress`. Certifique-se de que introduz "AzureAD", pois é um nome de domínio fixo. Em seguida, introduza o endereço de e-mail do Azure Active Directory. Por exemplo, introduza `AzureAD\user@contoso.onmicrosoft.com`.

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Se estiver a utilizar uma conta do Azure Active Directory para o modo de quiosque, certifique-se de que introduz `AzureAD\user@yourorganization.com`.

- **O modelo de utilizador de aplicação ID (AUMID) da aplicação**: Introduza o AUMID da aplicação de local público. Para saber mais, veja [Find the Application User Model ID of an installed app (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

#### <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

Os [quiosques de várias aplicações](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) utilizam uma configuração de quiosque que apresenta uma lista de aplicações permitidas e outras definições. 

Utilize o botão **Adicionar** para criar uma configuração de quiosque ou selecionar uma configuração existente. Em seguida, introduza as seguintes definições:

- **Nome da configuração do quiosque**: Introduza um nome amigável utilizado para identificar a configuração.

- **Aplicações do quiosque**: Introduza as aplicações que estão disponíveis no menu Iniciar. As aplicações que adicionar são as únicas aplicações que o utilizador pode abrir.

  - **Tipo de aplicação**: Escolha o tipo de aplicação de local público:
    - **Aplicação Win32**: Uma aplicação de ambiente de trabalho tradicional. Precisará do nome do caminho absoluto do ficheiro executável, relativamente ao dispositivo.
    - **Aplicação UWP**: Uma aplicação Universal do Windows. Precisará do [AUMID da aplicação](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Identificador**: Introduza o caminho absoluto do ficheiro executável (aplicações Win32) ou o [AUMID da aplicação](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicações UWP).

- **Barra de tarefas**: Optar por **habilitar** (Mostrar) a barra de tarefas, ou mantê-lo **não configurada** (oculto) no quiosque.

- **Esquema do menu Iniciar**: Introduza um ficheiro XML que descreve a forma como as aplicações são apresentadas no menu Iniciar. O artigo [Customize and export Start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) fornece algumas orientações e um ficheiro XML de exemplo.

  [Criar um quiosque do Windows 10 que executa aplicações](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) fornece mais detalhes sobre como utilizar e criar ficheiros XML.

- **Utilizadores atribuídos**: Adicione um ou mais contas de utilizador que podem utilizar as aplicações que adicionar. Quando a conta iniciar sessão, apenas as aplicações definidas na configuração estarão disponíveis. A conta pode ser local do dispositivo ou uma conta do Azure AD associada à aplicação de quiosque.

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `domain\user@tenant.com`.

## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado

- **Notificações do Centro de ação (apenas móvel)**: Notificações do Centro de ação permite que aparecem no ecrã de bloqueio do dispositivo (apenas Windows 10 Mobile).
- **O URL da imagem de ecrã (apenas ambiente de trabalho) bloqueado**: Introduza o URL para uma imagem em formato JPEG que é utilizado como a imagem de fundo do ecrã de bloqueio do Windows. Esta definição bloqueia a imagem. A imagem não pode ser alterada posteriormente.
- **Tempo limite do ecrã configurável pelo utilizador (apenas móvel)**: Permite que os utilizadores configurem a quantidade de tempo 
- **Cortana no ecrã bloqueado (apenas ambiente de trabalho)**: Não permitir que o usuário interaja com a Cortana quando o dispositivo estiver no ecrã de bloqueio (apenas ambiente de trabalho do Windows 10).
- **Notificações de alerta no ecrã bloqueado**: Bloquear mensagens de alerta que mostra no ecrã de bloqueio do dispositivo.
- **Tempo limite (apenas móvel) de ecrã**: Especifica o tempo em segundos depois do ecrã bloquear, quando irá desativar.

## <a name="messaging"></a>Sistema de mensagens

- **Sincronização (apenas móvel) de mensagens**: Desativar as mensagens em qualquer lugar e a cópia de segurança de mensagem de texto e de restauro.
- **MMS (apenas móvel)**: Desative a funcionalidade de envio/receção de MMS no dispositivo.
- **RCS (apenas móvel)**: Desative a funcionalidade de envio/receção para serviços de comunicação avançados no dispositivo.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

### <a name="start-experience"></a>Experiência de início

- **Iniciar o Microsoft Edge com**: Escolha quais páginas abrem quando o Microsoft Edge é iniciado. As opções são:
  - **Páginas iniciais**: Início do Microsoft Edge com a página inicial padrão definido pelo sistema operacional
  - **Nova página de separador**: Tudo o que é definido de carga do Microsoft Edge a **URL de página novo separador** definição
  - **Última página da sessão**: Microsoft Edge carrega a última página de sessão 
  - **Página inicial de personalizado**: Microsoft Edge carrega a página de início definida pelo administrador de TI
- **O utilizador pode alterar a páginas iniciais**: **Permitir** permite que os utilizadores alterem as páginas iniciais. Os administradores podem usar o `EdgeHomepageUrls` para introduzir as páginas de início que os utilizadores veem por predefinição ao abrir o Microsoft Edge. **Não configurado** bloqueia os utilizadores de alterar as páginas de início.
- **Novo URL da página de separador**: Introduza o URL para abrir a página novo separador. Por exemplo, introduza `https://www.bing.com`.
- **Abra o conteúdo da web na página nova guia**: Escolher **bloco** para impedir o Microsoft Edge de abertura de um site num novo separador. Quando bloqueado, o novo separador Abrir em branco. **Não configurado** utiliza o comportamento padrão do sistema operacional no dispositivo, que pode permitir que os usuários escolham o que é mostrado.
- **Botão início**: Escolha o que acontece quando o botão de base está selecionado. As opções são:
  - **Páginas iniciais**: A opção que selecionou para o **iniciar o Microsoft Edge com** abre-se a definição
  - **Nova página de separador**: A opção que selecionou para o **URL de página novo separador** abre-se a definição
  - **URL de botão personalizado Home**: A opção que selecionou para o **URL de botão de casa** abre-se a definição
  - **Botão de ocultar Home**: Oculta o botão de início
- **O utilizador pode alterar o botão Home**: **Permitir** permite que os utilizadores alterem o botão de início. As alterações do utilizador substituem as definições de administrador para o botão de início. **Não configurado** utiliza o comportamento padrão do sistema operacional no dispositivo, que pode bloquear os utilizadores de alterar a forma como o administrador configurado o botão de início.
- **Mostrar página de tela de apresentação**: **Bloco** pára a página de introdução de mostrar o primeiro tempo executa o Microsoft Edge. Esta funcionalidade permite às empresas, como as que estão inscritas em zero configurações de emissões, bloquear esta página. **Não configurado** mostra a página de introdução.
  - **Execute primeiro o URL de experiência**: Introduza o URL de página para mostrar na primeira vez que um utilizador executa o Microsoft Edge (apenas Windows 10 Mobile).
- **Pop-ups**: Escolher **bloco** para parar de janelas pop-up no browser. Aplica-se apenas a computadores com o Windows 10. **Não configurado** permite que os pop-ups do browser.
- **Enviar tráfego da intranet para o Internet Explorer**: **Permitir** permite que os utilizadores abram sites da intranet no Internet Explorer em vez do Microsoft Edge (apenas ambiente de trabalho do Windows 10). **Não configurado** permite que os utilizadores utilizem o Microsoft Edge.
- **Localização de lista de sites de modo de empresa**: Introduza o URL que inclua uma lista de sites que abrem no modo empresarial. Os utilizadores não é possível alterar o dessa lista. Aplica-se apenas a computadores com o Windows 10.
- **Mensagem ao abrir sites no Internet Explorer**: Utilize esta definição para configurar o Microsoft Edge para mostrar uma notificação antes de um site é aberta no Internet Explorer 11. As opções são:
  - **Não configurado**: É utilizado o comportamento padrão do sistema operacional, que não pode mostrar uma mensagem.
  - **Mostrar mensagem sem opção de abrir sites no Microsoft Edge**: Mostre a mensagem ao abrir sites no IE. Os sites abertos no IE. Não há uma opção para abrir sites no Microsoft Edge.
  - **Mostrar a mensagem ao abrir sites no Microsoft Edge**: Mostre a mensagem ao abrir sites no IE. A mensagem inclui uma **continue a utilizar no Microsoft Edge** ligar para os utilizadores possam escolher o Microsoft Edge em vez do IE.

  > [!IMPORTANT]
  > Esta definição necessita que ative a **configurar a lista de sites do modo empresarial** definição, o **enviar todos os sites de intranet para o Internet Explorer 11** definição ou ambas as definições.

- **Lista de compatibilidade Microsoft**: **Bloco** impede que a lista de compatibilidade Microsoft no Microsoft Edge. Esta lista da Microsoft Ajuda Microsoft Edge apresente corretamente os sites com problemas de compatibilidade conhecidos. **Não configurado** permite o uso de uma lista de compatibilidade da Microsoft.
- **Pré-carregar páginas de início e de página novo separador**: Escolher **bloco** para impedir o pré-carregamento de páginas de início e a nova página de separador do Microsoft Edge. Pré-carregamento minimiza o tempo para iniciar o Microsoft Edge e carregar um novo separador. **Não configurado** utiliza o comportamento padrão de sistema operacional, que pode ser pré-carregar essas páginas.
- **Iniciará páginas de início e de página novo separador**: Escolher **bloco** para impedir que o Microsoft Edge previamente iniciar as páginas de início e a nova página de separador. Pré-início ajuda o desempenho do Microsoft Edge e minimiza o tempo necessário para iniciar o Microsoft Edge. **Não configurado** utiliza o comportamento padrão de sistema operacional, que pode ser iniciará a essas páginas.

### <a name="favorites-and-search"></a>Favoritos e pesquisar

- **Barra de Favoritos**: Escolha o que acontece na barra de Favoritos em qualquer página do Microsoft Edge. As opções são:
  - **Não configurado**: Utiliza o comportamento padrão de sistema operacional, que pode ser ocultar a barra de Favoritos em todas as páginas. O utilizador pode alterar esta definição.
  - **Ocultar**: Oculta a barra de Favoritos em todas as páginas. O utilizador não é possível alterar esta definição.
  - **Mostrar**: Mostra a barra de Favoritos em todas as páginas. O utilizador não é possível alterar esta definição.
- **Lista de Favoritos**: Adicione uma lista de URLs para o ficheiro de Favoritos. Por exemplo, adicionar `http://contoso.com/favorites.html`.
- **Restringir alterações aos Favoritos**: **Bloco** para impedir que os utilizadores de adicionarem, importar, classificação ou editar a lista de Favoritos. **Não configurado** utiliza a predefinição do sistema operacional, que pode permitir que os utilizadores alterar a lista.
- **Sincronizar favoritos entre browsers da Microsoft (apenas ambiente de trabalho)**: **Exigir** força do Windows para sincronizar favoritos entre o Internet Explorer e o Microsoft Edge. Adições, eliminações, modificações e alterações de ordem nos favoritos são partilhadas entre browsers.  **Não configurado** utiliza a predefinição de SO, o que poderá que os utilizadores para sincronizar favoritos entre browsers.
- **Motor de busca predefinido**: Escolha o motor de busca predefinido no dispositivo. Os utilizadores finais podem alterar este valor em qualquer altura. As opções são:
  - Predefinição
  - Bing
  - Google
  - Yahoo
  - Valor personalizado
- **Sugestões de pesquisa**: **Não configurado** permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa na barra de endereço. **Bloco** impede que esta funcionalidade.

### <a name="privacy-and-security"></a>Privacidade e segurança

- **Navegação inPrivate**: **Bloco** impede que os utilizadores finais abrir sessões de Navegação InPrivate. **Não configurado** permite esta funcionalidade.
- **Guardar o histórico de navegação**: **Bloco** impede que o Microsoft Edge a guardar o histórico de navegação. **Não configurado** permitir guardar o histórico de navegação.
- **Limpar dados de navegação à saída (apenas ambiente de trabalho)**: **Exigir** limpa o histórico e dados de navegação quando o utilizador sai do Microsoft Edge. **Não configurado** utiliza o padrão de sistema operacional, o que pode colocar em cache os dados de navegação.
- **Sincronizar as definições do browser entre dispositivos do utilizador**: Escolha como pretende sincronizar as definições do browser entre dispositivos. As opções são:
  - **Permitir**: Permitir a sincronização de definições do browser Microsoft Edge entre dispositivos do utilizador
  - **Bloquear e ativar a substituição de utilizador**: Bloquear a sincronização de definições do browser Microsoft Edge entre dispositivos do utilizador. Os utilizadores podem substituir esta definição.
  - **Bloco**: Bloquear a sincronização de configuração de browser do Microsoft Edge entre dispositivos do utilizador. Os utilizadores não podem substituir esta definição.
- **Gestor de palavra-passe**: **Bloco** desativa a funcionalidade Gestor de palavra-passe do Microsoft Edge. **Não configurado** permite esta funcionalidade.
- **Cookies**: Escolha como os cookies são processados no navegador da web. As opções são:
  - **Permitir**: Cookies são armazenados no dispositivo.
  - **Bloquear todos os cookies**: Cookies não são armazenados no dispositivo.
  - **Bloquear apenas cookies de terceiros**: Os cookies de parceiro de terceiros ou não são armazenados no dispositivo.
- **Preenchimento automático**: **Bloco** desativa a funcionalidade de preenchimento automático no dispositivo. **Não configurado** permite que os utilizadores alterem as definições no browser (apenas ambiente de trabalho do Windows 10).
- **Enviar cabeçalhos de realizar rastreio não**: **Não configurado** requer que os dispositivos para enviar cabeçalhos para não realizar-rastreio em Web sites que pedem informações de controlo (recomendada). Escolher **bloco** para impedir que o dispositivo de enviar esses cabeçalhos, que permite que os Web sites controlar o utilizador.
- **Endereço IP de localhost do WebRtc**: **Bloco** impede que o endereço IP localhost de utilizadores que está a ser mostrado quando efetuar chamadas telefónicas utilizando a protocolo RTC da web. **Não configurado** permite aos utilizadores, endereço IP de localhost ser mostrada quando efetuar chamadas telefónicas utilizando esse protocolo.
- **Recolha de dados do mosaico dinâmico**: Escolher **bloco** para impedir o Windows de recolher informações do mosaico dinâmico está afixado um site no menu Iniciar do Microsoft Edge. **Não configurado** permite que estas informações a recolher.
- **Utilizador pode ignorar erros de certificado**: **Bloco** impede que os utilizadores aceder a sites que têm erros SSL ou TLS. **Não configurado** permite aos utilizadores aceder estes sites.

### <a name="additional"></a>Adicionais

- **Browser Microsoft Edge (apenas móvel)**: Escolher **bloco** para impedir a utilização do Microsoft Edge no dispositivo. Se bloquear o Microsoft Edge, as definições individuais só se aplicam a área de trabalho. **Não configurado** permite o uso do browser Microsoft Edge no dispositivo.
- **Lista pendente (apenas ambiente de trabalho) da barra de endereço**: **Bloco** interrompe o Microsoft Edge de mostrar uma lista de sugestões numa lista pendente, quando escreve. Esta opção ajuda a minimizar a largura de banda de rede entre o Microsoft Edge e os serviços da Microsoft. **Não configurado** permite que o Microsoft Edge mostrar uma lista de sugestões.
- **Ecrã inteiro**: Escolher **bloco** para impedir que o Microsoft Edge de apenas o que mostra o conteúdo da web e ocultar o Microsoft Edge (modo de ecrã inteiro). **Não configurado** utiliza a predefinição do sistema operacional, que permite que o Microsoft Edge utilizar o modo de ecrã inteiro.
- **Sinalizadores**: **Bloco** impede que os utilizadores finais acedam a `about:flags` página no Microsoft Edge, que inclui o desenvolvedor e as definições experimentais. **Não configurado** utiliza a predefinição do sistema operacional, que poderá permitir o acesso a `about:flags` página.
- **Ferramentas de programação**: **Bloco** impede que os utilizadores finais abrir as ferramentas de desenvolvimento do Microsoft Edge. **Não configurado** permite aos utilizadores abrir as ferramentas de desenvolvimento.
- **Extensões**: **Não configurado** permite aos utilizadores finais instalar as extensões do Microsoft Edge no dispositivo. **Bloco** impede a instalação.
- **Extensões de desenvolvedor de Sideload**: **Bloco** impede que o Microsoft Edge de sideload, que instala e executa as extensões não verificadas com o **carregam extensões** funcionalidade. **Não configurado** utiliza a predefinição do sistema operacional, o que poderá permitir o sideload.
- **Necessário extensões**: Escolha quais as extensões que não podem ser desativadas pelos usuários finais na Microsoft Edge. Introduza os nomes da família de pacote e selecione **adicionar**. [Localizar um nome de família de pacotes (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) listas fornece algumas diretrizes.

  Também pode **importação** um ficheiro CSV que inclui os nomes da família de pacotes.

- **JavaScript**: Escolher **bloco** para impedir que os scripts em Java no browser em execução no dispositivo. **Não configurado** permite que scripts, como Javascript, sejam executados no browser Microsoft Edge.

## <a name="network-proxy"></a>Proxy de rede

- **Detetar automaticamente as definições de proxy**: Quando ativada, o dispositivo tenta localizar o caminho para um script PAC.
- **Utilizar script de proxy**: Selecione esta opção para introduzir um caminho para um script de PAC para configurar o servidor proxy.
  - **URL de endereço do script de configuração**: Introduza o URL de um script de PAC que pretende utilizar para configurar o servidor proxy.
- **Utilizar um servidor manual proxy**: Selecione esta opção para introduzir manualmente as informações do servidor proxy.
  - **Endereço**: Introduza o nome ou endereço IP do servidor proxy.
  - **Número de porta**: Introduza o número de porta do servidor proxy.
  - **Exceções de proxy**: Introduza os URLs que não tem de utilizar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
  - **Ignorar servidor proxy para endereço local**: Se não quiser utilizar o servidor proxy para endereços locais na sua intranet, ative esta opção.

## <a name="password"></a>Palavra-passe

- **palavra-passe**: Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
  - **Tipo de palavra-passe obrigatório**: Especifica se a palavra-passe tem de ser numérica único ou de alfanuméricos.
  - **Comprimento mínimo da palavra-passe**: Aplica-se apenas ao Windows 10 Mobile.
  - **Número de falhas de início de sessão antes de limpar o dispositivo**: Para dispositivos com o Windows 10: Se o dispositivo tiver o BitLocker ativado, será colocado no modo de recuperação do BitLocker após o início de sessão falha o número de vezes que especificar. Se o dispositivo não for o BitLocker ativado, em seguida, esta definição não se aplica. Para dispositivos com Windows 10 Mobile: Após o início de sessão falha o número de vezes que especificar, o dispositivo ser apagado.
  - **Máximo de minutos de inatividade até o ecrã bloquear**: Especifica o período de tempo durante o qual o dispositivo tem de estar inativo antes de o ecrã ser bloqueado.
  - **Expiração de palavra-passe (dias)**: Especifica o período de tempo após o qual a palavra-passe do dispositivo tem de ser alterada.
  - **Impedir a reutilização de palavras-passe anteriores**: Especifica o número de palavras-passe utilizadas anteriormente que são memorizadas pelo dispositivo.
  - **Exigir palavra-passe quando o dispositivo regressa do Estado de inatividade (apenas móvel)**: Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo (apenas Windows 10 Mobile).
  - **Palavras-passe simples**: Permite-lhe permitir a utilização de palavras-passe simples, como 1111 e 1234. Esta definição também permite ou bloqueia a utilização de palavras-passe por imagem do Windows.

## <a name="per-app-privacy-exceptions"></a>Exceções de privacidade por aplicação

Pode adicionar aplicações que devem ter um comportamento de privacidade diferente do que definiu em “Privacidade predefinida”.

- **Nome do pacote**: Nome de família do pacote de aplicação.
- **Nome da aplicação**: O nome da aplicação.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se esta aplicação pode aceder o nome de utilizador, imagem e outras informações de contacto.
- **Aplicações em segundo plano**: Defina se esta aplicação pode ser executado em segundo plano.
- **Calendário**: Defina se esta aplicação pode aceder ao calendário.
- **Histórico de chamadas**: Defina se esta aplicação pode aceder o meu histórico de chamadas.
- **Câmara**: Defina se esta aplicação pode aceder à câmara.
- **Contactos**: Defina se esta aplicação pode aceder aos contactos.
- **e-mail**: Defina se esta aplicação pode aceder e enviar mensagem de e-mail.
- **Localização**: Defina se esta aplicação pode aceder a informações de localização.
- **Mensagens**: Defina se esta aplicação pode ler ou enviar SMS ou MMS.
- **Microfone**: Defina se esta aplicação pode utilizar o microfone.
- **Equipe do Motion**: Defina se esta aplicação pode aceder a informações de movimento do dispositivo.
- **Notificações**: Defina se esta aplicação pode aceder a notificações.
- **Telefone**: Defina se esta aplicação pode aceder ao telefone.
- **Rádios**: Algumas aplicações utilizam rádios (por exemplo, Bluetooth) no seu dispositivo para enviar e receber dados e tem de ativar ou desativar a estes rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se esta aplicação pode aceder às suas tarefas.
- **Dispositivos fidedignos**: Escolha se esta aplicação pode utilizar dispositivos fidedignos, que é o hardware que já ligou ou hardware que é fornecido com o dispositivo. Por exemplo, utilize o TVs, projetores etc., como dispositivos fidedignos.
- **Comentários e diagnóstico**: Defina se esta aplicação pode aceder a informações de diagnóstico.
- **Sincronização com dispositivos**: Escolha se esta aplicação pode partilhar e sincronizar informações com dispositivos sem fios que não sejam emparelham especificamente com o dispositivo automaticamente.

## <a name="personalization"></a>Personalização

- **URL da imagem de fundo (apenas ambiente de trabalho)**: Introduza o URL para uma imagem em formato JPEG que pretende utilizar como a imagem de fundo de ambiente de trabalho Windows. Os utilizadores não podem alterar a imagem.

## <a name="printer"></a>Impressora

- **Impressoras**: Lista de impressoras locais que foram adicionados.
- **Impressora predefinida**: Defina a impressora predefinida.
- **Acesso de utilizador para adicionar novas impressoras**: Permitir ou bloquear a utilização de impressoras locais.

## <a name="privacy"></a>Privacidade

- **Personalização de entrada**: Não permite a utilização dos serviços de fala baseados na cloud para aplicações Cortana, ditado ou Microsoft Store. Se permitir estes serviços, a Microsoft recolherá os dados de voz para melhorar o serviço.
- **Aceitação automática das solicitações de consentimento de utilizador de emparelhamento e privacidade**: Permitir que o Windows aceite automaticamente de emparelhamento e privacidade as mensagens de consentimento ao executar as aplicações.
- **Publicar as atividades do utilizador**: **Bloco** impede que as experiências compartilhadas e deteção de recursos recentemente utilizados no comutador de tarefas.
- **Apenas atividades locais**: **Bloco** impede que as experiências compartilhadas e a deteção de recursos recentemente utilizados no comutador de tarefas, com base na atividade local.

Pode configurar as informações que podem aceder a todas as aplicações no dispositivo. Pode definir exceções numa base por aplicação através de **Exceções de privacidade por aplicação**.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se esta aplicação pode aceder o nome de utilizador, imagem e outras informações de contacto.
- **Aplicações em segundo plano**: Defina se esta aplicação pode ser executado em segundo plano.
- **Calendário**: Defina se esta aplicação pode aceder ao calendário.
- **Histórico de chamadas**: Defina se esta aplicação pode aceder o meu histórico de chamadas.
- **Câmara**: Defina se esta aplicação pode aceder à câmara.
- **Contactos**: Defina se esta aplicação pode aceder aos contactos.
- **e-mail**: Defina se esta aplicação pode aceder e enviar mensagem de e-mail.
- **Localização**: Defina se esta aplicação pode aceder a informações de localização.
- **Mensagens**: Defina se esta aplicação pode ler ou enviar SMS ou MMS.
- **Microfone**: Defina se esta aplicação pode utilizar o microfone.
- **Equipe do Motion**: Defina se esta aplicação pode aceder a informações de movimento do dispositivo.
- **Notificações**: Defina se esta aplicação pode aceder a notificações.
- **Telefone**: Defina se esta aplicação pode aceder ao telefone.
- **Rádios**: Algumas aplicações utilizam rádios (por exemplo, Bluetooth) no seu dispositivo para enviar e receber dados e tem de ativar ou desativar a estes rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se esta aplicação pode aceder às suas tarefas.
- **Dispositivos fidedignos**: Escolha se esta aplicação pode utilizar dispositivos fidedignos. Dispositivos fidedignos é hardware que já ligou ou hardware que vem com o dispositivo. Por exemplo, utilize e assim por diante TVs, projetores, como dispositivos fidedignos.
- **Comentários e diagnóstico**: Escolha se esta aplicação pode aceder a informações de diagnóstico.
- **Sincronização com dispositivos** – defina se esta aplicação pode partilhar e sincronizar automaticamente informações com dispositivos sem fios que não sejam emparelhados especificamente com o PC, tablet ou telefone.

## <a name="projection"></a>Projeção

- **Entrada de utilizador de recetores de ecrã sem fios**: Utilizador de blocos de entrada de recetores de ecrã sem fios.
- **Projeção para este PC**: Impede outros dispositivos de localizar o PC para projeção.
- **Exigir PIN para emparelhamento**: Exigir um PIN ao ligar a um dispositivo de projeção.

## <a name="reporting-and-telemetry"></a>Relatórios e Telemetria

- **Partilhar dados de utilização**: Escolha o nível de dados de diagnóstico que são submetidos. As opções são:
  - Segurança
  - Básica
  - Avançada
  - Completo
- **Enviar dados para o Microsoft 365 Analytics de navegação do Microsoft Edge**: Para utilizar esta funcionalidade, defina o **partilhar dados de utilização** configurações para **avançado** ou **completa**. Esta funcionalidade controla que dados Microsoft Edge envia para o Microsoft 365 Analytics dos dispositivos da empresa com um ID comercial configurado. As opções são:
  - **Não configurado**: Utiliza o padrão de sistema operacional, o que não pode enviar quaisquer dados de histórico de navegação
  - **Enviar apenas dados de intranet**: Permite ao administrador enviar o histórico de dados de intranet
  - **Enviar apenas dados de internet**: Permite ao administrador enviar o histórico de dados da internet
  - **Enviar dados de intranet e internet**: Permite ao administrador enviar o histórico de dados de intranet e internet
- **Servidor de proxy da telemetria**: Introduza o nome de domínio completamente qualificado (FQDN) ou o endereço IP de um servidor proxy para reencaminhar pedidos de telemetria, através de uma ligação de Secure Sockets Layer (SSL) e experiências do usuário conectado. O formato para esta definição é *servidor*:*porta*. Se o proxy nomeado falhar ou se não existir um proxy que introduziu quando esta política está ativada, os dados de telemetria e experiências de utilizador ligado não são enviados e permanecem no dispositivo local.

  Formatos de exemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Pesquisa

- **Pesquisa segura (apenas móvel)**: Controle a forma como a Cortana filtra o conteúdo para adultos nos resultados da pesquisa. Pode selecionar **Rigoroso**, **Moderado** ou permitir que o utilizador final escolha as suas próprias definições.
- **Mostrar os resultados da web na procura**: Bloquear ou permitir que os resultados da web são apresentados nas pesquisas feitas no dispositivo.

## <a name="start"></a>Iniciar,

- **Esquema do menu Iniciar**: Para personalizar o menu Iniciar em dispositivos de ambiente de trabalho, pode carregar um ficheiro XML que inclui suas personalizações, incluindo a ordem que as aplicações forem apresentadas, e muito mais. Os utilizadores não é possível alterar o esquema do menu Iniciar que introduzir.
- **Afixar sites a mosaicos no menu Iniciar**: Importar imagens a partir do Microsoft Edge, que são apresentados como ligações no menu Iniciar do Windows para dispositivos de ambiente de trabalho.
- **Remover aplicações da barra de tarefas**: Escolher **bloco** para interromper o usuário de remover aplicações a partir da barra de tarefas.
- **Mudança rápida de utilizador**: Escolher **bloco** para evitar a alternância entre os utilizadores que tenham sessão iniciados em simultâneo sem fazer logoff.
- **Aplicações mais utilizadas**: Escolher **bloco** para ocultar as aplicações mais utilizadas de mostrar no menu Iniciar. Também desativa o seletor correspondente na aplicação Definições.
- **Aplicações adicionadas recentemente**: Escolher **bloco** para ocultar aplicações adicionadas recentemente de mostrar no menu Iniciar. Também desativa o seletor correspondente na aplicação Definições.
- **Iniciar modo de ecrã**: Escolha a forma como é apresentado o ecrã de início. Opte por mostrar como **Ecrã inteiro** ou **Ecrã não inteiro**.
- **Recentemente, abrir itens em listas de atalhos**: Escolher **bloco** para ocultar as listas de atalhos recentes do que está a ser mostrada no menu Iniciar e barra de tarefas. Também desativa o seletor correspondente na aplicação Definições.
- **Lista de aplicações**: Escolha a forma como a aplicação de definições é mostrada. As opções são: 
  - Fechar
  - Fechar e desativar a aplicação Definições 
  - Remover e desativar a aplicação Definições
- **Botão de energia**: Escolher **bloco** para ocultar o botão de energia do que mostra no menu Iniciar.
- **Mosaico de utilizador**: Escolher **bloco** para ocultar o mosaico de utilizador de mostrar no menu Iniciar.
  - **Bloqueio**: Escolher **bloco** para ocultar o `Lock` opção de mostrar no mosaico de utilizador no menu Iniciar.
  - **Terminar sessão**: Escolher **bloco** para ocultar o `Sign out` opção de mostrar no mosaico de utilizador no menu Iniciar.
- **Encerrar**: Escolher **bloco** para ocultar a `Update and shut down` e `Shut down` opções de mostrar no botão de energia no menu Iniciar.
- **Modo de suspensão**: Escolher **bloco** para ocultar o `Sleep` opção de mostrar no botão de energia no menu Iniciar.
- **Hibernar**: Escolher **bloco** para ocultar o `Hibernate` opção de mostrar no botão de energia no menu Iniciar.
- **Mudar de conta**: Escolher **bloco** para ocultar o `Switch account` de mostrar o utilizador mosaico no menu Iniciar.
- **Opções de reinício**:  Escolher **bloco** para ocultar a `Update and restart` e `Restart` opções de mostrar no botão de energia no menu Iniciar.
- **Documentos em Iniciar**: Ocultar ou mostrar a pasta documentos no menu Iniciar do Windows.
- **Transferências em Iniciar**: Ocultar ou mostrar a pasta transferências no menu Iniciar do Windows.
- **Explorador de ficheiros em Iniciar**: Ocultar ou mostrar a aplicação do Explorador de ficheiros no menu Iniciar do Windows.
- **Grupo doméstico em Iniciar**: Ocultar ou mostrar a pasta grupo doméstico no menu Iniciar do Windows.
- **Música em Iniciar**: Ocultar ou mostrar a pasta Música no menu Iniciar do Windows.
- **Rede em Iniciar**: Ocultar ou mostrar a pasta de rede no menu Iniciar do Windows.
- **Pasta pessoal em Iniciar**: Ocultar ou mostrar a pasta pessoal no menu Iniciar do Windows.
- **Imagens em Iniciar**: Ocultar ou mostrar a pasta de imagens no menu Iniciar do Windows.
- **Definições em Iniciar**: Ocultar ou mostrar a aplicação de definições no menu Iniciar do Windows.
- **Vídeos em Iniciar**: Ocultar ou mostrar a pasta dos vídeos no menu Iniciar do Windows.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para o Microsoft Edge**: Ative o Microsoft Edge SmartScreen para aceder ao site e transferências de ficheiros.
- **Acesso a site malicioso**: Impedir que os utilizadores ignorem os avisos do filtro do Windows Defender SmartScreen e impeça-os de aceder ao site.
- **Transferência de ficheiros não verificados**: Impedir que os utilizadores ignorem os avisos do filtro do Windows Defender SmartScreen e impeça-os de transferir ficheiros não verificados.

## <a name="windows-spotlight"></a>Destaque do Windows

- **Destaque do Windows**: Utilize esta definição para bloquear todas as funcionalidades do destaque do Windows em dispositivos Windows 10. Se bloquear esta definição, as seguintes definições não estão disponíveis:
  - **Destaque do Windows no ecrã de bloqueio**: Impedi o destaque do Windows de apresentar informações no ecrã de bloqueio do dispositivo.
  - **Sugestões de terceiros no destaque do Windows**: Impedi o destaque do Windows de sugerir conteúdos que não está publicado pela Microsoft.
  - **Funcionalidades do consumidor**: Começar a permite-lhe bloquear funcionalidades do consumidor como sugestões de menu e notificações de associação.
  - **Dicas do Windows**: Permite-lhe bloquear a apresentação no Windows de sugestões pop-up.
  - **Destaque do Windows no Centro de ação**: Sugestões do destaque do Windows bloquear como nova aplicação ou o conteúdo de segurança de aparecer no Centro de ação do Windows.
  - **Personalização do destaque do Windows**: Será interrompido o destaque do Windows personalize os resultados com base na utilização de um dispositivo.
  - **Experiência de boas-vindas Windows**: Bloquear a experiência de boas-vindas do Windows que mostra informações sobre funcionalidades novas ou atualizadas.

## <a name="windows-defender-antivirus"></a>Antivírus do Windows Defender

- **Monitorização em tempo real**: Permite a análise em tempo real de software maligno, spyware e outro software indesejável.
- **Monitorização de comportamento**: Permite que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos.
- **Network Inspection System (NIS)**: NIS ajuda a proteger os dispositivos contra exploits baseados na rede. Utiliza as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e bloquear tráfego malicioso.
- **Analisar todas as transferências**: Controla se o Defender analisa todos os ficheiros transferidos da Internet.
- **Analisar scripts carregados em browsers da Microsoft**: Permite que o Defender analise os scripts que são utilizados no Internet Explorer.
- **Acesso do utilizador final ao Defender**: Controla se a interface de utilizador do Windows Defender está ocultada dos utilizadores finais. Quando esta definição for alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.
- **Intervalo de atualização de assinatura (em horas)**: Especifique o intervalo no qual o Defender verifica para novos ficheiros de assinatura.
- **Monitorizar a atividade de programas e ficheiros**: Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos.
- **Dias antes de eliminar o software malicioso em quarentena**: Permite que o Defender continue a controlar o software maligno resolvido durante o número de dias que especificar, para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias para **0**, software maligno permanece na pasta de quarentena e não são automaticamente removido.
- **Limite de utilização da CPU durante uma análise**: Permite limitar a quantidade de CPU que as análises estão autorizadas a utilizar (de **1** a **100**).
- **Verificar arquivos mortos**: Permite que o Defender analise os ficheiros arquivados, tais como ficheiros Zip ou Cab.
- **Analisar mensagens de correio recebidas**: Permite que o Defender analise mensagens de e-mail quando chegam ao dispositivo.
- **Analisar unidades amovíveis durante uma análise completa**: Permite que o Defender analise unidades amovíveis, como pens USB.
- **Analisar unidades de rede mapeadas durante uma análise completa**: Permite que o Defender analise ficheiros em unidades de rede mapeadas.
  Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
- **Analisar ficheiros abertos a partir de pastas de rede**: Permite que o Defender analise ficheiros em unidades de rede partilhadas (por exemplo, ficheiros acedidos a partir de um caminho UNC). Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
- **Proteção da cloud**: Permite ou impede que o Serviço de Proteção Ativa Microsoft receba informações sobre a atividade de software maligno nos dispositivos geridos por si. Estas informações são utilizadas para melhorar o serviço no futuro.
- **Pedir aos utilizadores antes da submissão de exemplo**: Controles se ficheiros potencialmente maliciosos que possam exigir análise adicional são automaticamente enviados à Microsoft.
- **Hora a realizar uma análise rápida diária**: Permite agendar uma análise rápida que ocorre diariamente à hora que selecionar.
- **Tipo de análise do sistema para executar**: Introduza o nível de análise é executada quando agendar uma análise do sistema.
- **Detetar aplicações potencialmente indesejadas**: Escolha o nível de proteção quando o Windows detecta potencialmente indesejável aplicações a partir de:
  - **Bloquear**
  - **Auditoria** para obter mais informações sobre aplicações potencialmente indesejadas, veja [detetar e bloquear aplicações potencialmente indesejável](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Ações sobre ameaças de software maligno detetado**: Utilize esta opção para escolher as ações que o Defender deve executar para cada nível de ameaça detetar (baixo, moderado, alto e grave). As opções são:
  - **Limpar**
  - **Quarentena**
  - **Remove**
  - **Permitir**
  - **Definido pelo utilizador**
  - **Bloquear**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusões do Antivírus do Windows Defender

- **Ficheiros e pastas a excluir de análises e da proteção em tempo real**: Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
- **Extensões de ficheiros a excluir de análises e proteção em tempo real**: Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Os ficheiros com estas extensões não são incluídos em análises em tempo real ou agendadas.
- **Processos a excluir de análises e da proteção em tempo real**: Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não são incluídos em análises em tempo real ou agendadas.

## <a name="next-steps"></a>Passos Seguintes

Para obter os detalhes técnicos adicionais de cada definição e quais as edições do Windows suportadas, veja [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referência de CSP de Políticas do Windows 10)
