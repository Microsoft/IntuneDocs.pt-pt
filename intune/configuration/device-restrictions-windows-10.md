---
title: Definições de restrição de dispositivos para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Consulte uma lista de todas as configurações e suas descrições para criar restrições de dispositivo em dispositivos Windows 10 e posteriores. Use essas configurações em um perfil de configuração para controlar capturas de tela, requisitos de senha, configurações de quiosque, aplicativos na loja, navegador Microsoft Edge, Microsoft defender, acesso à nuvem, menu iniciar e muito mais em Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78daf56f7e1d22b88d7134ac6cea86f1d999f0c6
ms.sourcegitcommit: 66e284fe092e19c1da72b4b770e45bf25ac7910c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74860252"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos usando o Intune

Este artigo lista e descreve todas as diferentes configurações que você pode controlar em dispositivos Windows 10 e mais recentes. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, definir regras de senha, personalizar a tela de bloqueio, usar o Microsoft defender e muito mais.

Essas configurações são adicionadas a um perfil de configuração de dispositivo no Intune e, em seguida, atribuídas ou implantadas em seus dispositivos Windows 10.

> [!Note]
> Nem todas as opções estão disponíveis em todas as edições do Windows. Para ver as edições com suporte, consulte os [CSPs da política](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (abre outro site da Microsoft).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

Essas configurações usam o [CSP da política do ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), que também lista as edições do Windows com suporte.

- **Loja de aplicativos** (somente dispositivos móveis): **não configurado** (padrão) permite que os usuários finais acessem a loja de aplicativos em dispositivos móveis. **Bloquear** impede o uso da loja de aplicativos.
- **Atualizar automaticamente os aplicativos da loja**: **não configurado** (padrão) permite que os aplicativos instalados do Microsoft Store sejam atualizados de forma automática. **Bloquear** impede que as atualizações sejam instaladas automaticamente.
- **Instalação de aplicativo confiável**: escolha se os aplicativos não Microsoft Store podem ser instalados, também conhecidos como Sideload. O Sideload está sendo instalado e, em seguida, executando ou testando um aplicativo que não é certificado pelo Microsoft Store. Por exemplo, um aplicativo que é interno somente à sua empresa. As opções são:
  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Bloquear**: impede o Sideload. Não é possível instalar aplicativos não Microsoft Store.
  - **Permitir**: permite Sideload. Os aplicativos não Microsoft Store podem ser instalados.
- **Desbloqueio do desenvolvedor**: permite que as configurações do desenvolvedor do Windows, como permitir que aplicativos Sideload sejam modificadas pelos usuários finais. As opções são:
  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Bloquear**: impede o modo de desenvolvedor e aplicativos de Sideload.
  - **Permitir**: permite o modo de desenvolvedor e aplicativos de Sideload.

  [Habilitar seu dispositivo para desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) tem mais informações sobre esse recurso.

- **Dados de aplicativo de usuário compartilhados**: escolha **permitir** para compartilhar dados de aplicativo entre diferentes usuários no mesmo dispositivo e com outras instâncias desse aplicativo. **Não configurado** (padrão) impede o compartilhamento de dados com outros usuários e outras instâncias do mesmo aplicativo.
- **Usar somente o repositório particular**: **permitir** que apenas os aplicativos sejam baixados de um armazenamento particular e não baixados do armazenamento público, incluindo um catálogo de varejo. **Não configurado** (padrão) permite que os aplicativos sejam baixados de um repositório particular e de um repositório público.
- **Inicialização do aplicativo originado do repositório**: o **bloqueio** desabilita todos os aplicativos que foram pré-instalados no dispositivo ou baixados do Microsoft Store. **Não configurado** (padrão) permite que esses aplicativos sejam abertos.
- **Instalar dados de aplicativo no volume do sistema**: **Bloquear** impede que os aplicativos armazenem dados no volume do sistema do dispositivo. **Não configurado** (padrão) permite que os aplicativos armazenem dados no volume de disco do sistema.
- **Instalar aplicativos na unidade do sistema**: **Bloquear** impede que os aplicativos sejam instalados na unidade do sistema no dispositivo. **Não configurado** (padrão) permite que os aplicativos sejam instalados na unidade do sistema.
- **DVR de jogos** (somente desktop): o **bloco** desabilita a gravação e a transmissão de jogos do Windows. **Não configurado** (padrão) permite a gravação e a difusão de jogos.
- **Aplicativos somente da loja**: essa configuração determina a experiência do usuário quando os usuários instalam aplicativos de locais diferentes do Microsoft Store. As opções são:

  - **Não configurado** (padrão): permite que os usuários finais instalem aplicativos de locais diferentes do Microsoft Store, incluindo aplicativos definidos em outras configurações de política.  
  - **Em qualquer lugar**: desativa as recomendações do aplicativo e permite que os usuários instalem aplicativos de qualquer local.  
  - **Somente armazenar**: força os usuários finais a instalar somente aplicativos do Microsoft Store.
  - **Recomendações**: ao instalar um aplicativo da Web que está disponível no Microsoft Store, os usuários veem uma mensagem recomendando que eles o baixem da loja.  
  - **Preferir armazenamento**: avisa os usuários quando eles instalam aplicativos de locais diferentes do Microsoft Store.

  [CSP do SmartScreen/EnableAppInstallControl](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Controle do usuário sobre instalações**: quando definido como **não configurado** (padrão), Windows Installer impedir que os usuários alterem as opções de instalação normalmente reservadas para administradores do sistema, como inserir o diretório para instalar os arquivos. **Bloquear** permite que os usuários alterem essas opções de instalação e alguns dos recursos de segurança de Windows Installer são ignorados.

  [CSP ApplicationManagement/MSIAllowUserControlOverInstall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Instalar aplicativos com privilégios elevados**: quando definido como **não configurado** (padrão), o sistema aplica as permissões do usuário atual quando instala programas que um administrador do sistema não implanta ou oferece. O **bloco** instrui Windows Installer a usar permissões elevadas ao instalar qualquer programa no sistema. Esses privilégios são estendidos para todos os programas.

  [CSP ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Aplicativos de inicialização**: Insira uma lista de aplicativos para abrir depois que um usuário entrar no dispositivo. Certifique-se de usar uma lista delimitada por ponto-e-vírgula de nomes de família de pacotes (PFN) de aplicativos do Windows. Para que essa política funcione, o manifesto nos aplicativos do Windows deve usar uma tarefa de inicialização.

  [CSP ApplicationManagement/LaunchAppAfterLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

Essas configurações usam a [política de conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) e os CSPs da [política de Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) , que também listam as edições do Windows com suporte.

- [CSP da política Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Canal de dados da rede celular**: escolha se os usuários finais podem usar dados, como navegar na Web, quando conectados a uma rede de celular. As opções são:
  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração. Os usuários finais podem desativá-lo.
  - **Bloquear**: não permitir o canal de dados da rede celular. Os usuários finais não podem ativá-lo.
  - **Allow (não editável)** : permite o canal de dados da rede celular. Os usuários finais não podem desativá-lo.

- **Roaming de dados**: o **bloco** impede o roaming de dados de celular no dispositivo. **Não configurado** (padrão) permite o roaming entre redes ao acessar dados.
- **VPN na rede celular**: **Bloquear** impede que o dispositivo acesse conexões VPN quando conectado a uma rede de celular. **Não configurado** (padrão) permite que a VPN use qualquer conexão, incluindo a rede celular.
- **Roaming de VPN na rede celular**: o **bloco** impede que o dispositivo acesse conexões VPN ao fazer roaming em uma rede de celular. **Não configurado** (padrão) permite conexões VPN durante o roaming.
- **Serviço de dispositivos conectados**: o **bloqueio** DESABILITA o componente de CDP (plataforma de dispositivos conectados). A CDP permite a descoberta e a conexão com outros dispositivos (por meio de Bluetooth/LAN ou nuvem) para dar suporte à inicialização de aplicativos remotos, mensagens remotas, sessões de aplicativos remotos e outras experiências entre dispositivos. **Não configurado** (padrão) permite o serviço de dispositivos conectados, que permite a descoberta e a conexão com outros dispositivos Bluetooth.
- **NFC**: **Block** impede recursos de comunicação a curta distância (NFC). **Não configurado** (padrão) permite que os usuários habilitem e configurem recursos de NFC no dispositivo.
- **Wi-Fi**: **Bloquear** impede que os usuários habilitem, configurem e usem conexões Wi-Fi no dispositivo. **Não configurado** (padrão) permite conexões Wi-Fi.
- **Conectar automaticamente a hotspots Wi-Fi**: **Bloquear** impede que dispositivos se conectem automaticamente a hotspots Wi-Fi. **Não configurado** (padrão) permite que os dispositivos se conectem automaticamente a hotspots Wi-Fi gratuitos e aceitem automaticamente quaisquer termos e condições para a conexão.
- **Configuração manual de Wi-Fi**: **Bloquear** impede que os dispositivos se conectem ao Wi-Fi fora das redes instaladas pelo servidor MDM. **Não configurado** (padrão) permite que os usuários finais adicionem e configurem seus próprios SSIDs de rede de conexões Wi-Fi.
- **Intervalo de verificação de Wi-Fi**: Insira com que frequência os dispositivos verificam redes Wi-Fi. Insira um valor de 1 (mais frequente) a 500 (menos frequente). O padrão é `0` (zero).

### <a name="bluetooth"></a>Bluetooth

Essas configurações usam o [CSP de política do Bluetooth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth); que também lista as edições do Windows com suporte.

- **Bluetooth**: **Bloquear** impede que os usuários habilitem o Bluetooth. **Não configurado** (padrão) permite Bluetooth no dispositivo.
- **Descoberta de Bluetooth**: o **bloqueio** impede que o dispositivo seja detectável por outros dispositivos habilitados para Bluetooth. **Não configurado** (padrão) permite que outros dispositivos habilitados para Bluetooth, como um headset, descubram o dispositivo.
- **Pré-emparelhamento Bluetooth**: **Bloquear** impede que dispositivos Bluetooth específicos sejam emparelhados automaticamente com um dispositivo de host. **Não configurado** (padrão) permite o emparelhamento automático com o dispositivo de host.
- **Anúncio de Bluetooth**: **Bloquear** impede que o dispositivo envie anúncios de Bluetooth. **Não configurado** (padrão) permite que o dispositivo envie anúncios de Bluetooth.
- **Serviços autorizados de Bluetooth**: **adicione** uma lista de perfis e serviços Bluetooth permitidos como cadeias de caracteres hexadecimais, como `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  O [Guia de uso do ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) tem mais informações sobre a lista de serviços.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

Essas configurações usam o [CSP de política de contas](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts); que também lista as edições do Windows com suporte.

- **Conta Microsoft**: **Bloquear** impede que os usuários finais associem um conta Microsoft ao dispositivo. **Não configurado** (padrão) permite adicionar e usar um conta Microsoft.
- **Não conta Microsoft**: **Bloquear** impede que os usuários finais adicionem contas que não sejam da Microsoft usando a interface do usuário. **Não configurado** (padrão) permite que os usuários adicionem contas de email que não estão associadas a um conta Microsoft.
- **Sincronização de configurações para conta Microsoft**: **não configurado** (padrão) permite que as configurações de dispositivo e aplicativo associadas a um conta Microsoft para sincronizar entre dispositivos. **Bloquear** impede esta sincronização.
- **Assistente de conexão de conta da Microsoft**: quando definido como **não configurado** (padrão), os usuários finais podem iniciar e parar o serviço de WLIDSVC ( **Assistente de conexão de conta da Microsoft** ). Esse serviço de sistema operacional permite que os usuários entrem em seus conta Microsoft. **Desabilitar** impede que os usuários finais controlem o serviço de assistente de conexão da Microsoft (WLIDSVC).

## <a name="cloud-printer"></a>Impressora em Cloud

Essas configurações usam o [CSP da política do EnterpriseCloudPrint](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint); que também lista as edições do Windows com suporte.

- **URL de descoberta de impressora**: Insira a URL para localizar impressoras de nuvem. Por exemplo, introduza `https://cloudprinterdiscovery.contoso.com`.
- **URL da autoridade de acesso à impressora**: Insira a URL do ponto de extremidade de autenticação para obter tokens OAuth. Por exemplo, introduza `https://azuretenant.contoso.com/adfs`.
- **GUID do aplicativo cliente nativo do Azure**: Insira o GUID de um aplicativo cliente com permissão para obter tokens OAuth do OAuthAuthority. Por exemplo, introduza `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI do recurso do serviço de impressão**: Insira o URI de recurso do OAuth para o serviço de impressão configurado no portal do Azure. Por exemplo, introduza `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Máximo de impressoras a serem consultadas**: Insira o número máximo de impressoras que você deseja consultar. O valor predefinido é `20`.
- **URI do recurso do serviço de descoberta de impressora**: Insira o URI de recurso do OAuth para o serviço de descoberta de impressora configurado no portal do Azure. Por exemplo, introduza `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Depois de configurar uma [impressão em nuvem híbrida do Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), você pode definir essas configurações e, em seguida, implantar em seus dispositivos Windows.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Aplicativo de configurações**: **Bloquear** impede que os usuários finais acessem o aplicativo de configurações do Windows. **Não configurado** (padrão) permite que os usuários abram o aplicativo configurações no dispositivo.
  - **System**: **Bloquear** impede o acesso à área do sistema do aplicativo de configurações. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
    - **Modificação das configurações de energia e suspensão** (somente desktop): o **bloqueio** impede que os usuários finais alterem as configurações de energia e suspensão no dispositivo. **Não configurado** (padrão) permite que os usuários alterem as configurações de energia e suspensão.
  - **Dispositivos**: **Bloquear** impede o acesso à área dispositivos do aplicativo configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Internet de rede**: **Bloquear** impede o acesso à rede & área da Internet do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Personalização**: o **bloco** impede o acesso à área de personalização do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Aplicativos**: **Bloquear** impede o acesso à área de aplicativos do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Contas**: **Bloquear** impede o acesso à área contas do aplicativo configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Hora e idioma**: **Bloquear** impede o acesso ao horário & área de linguagem do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
    - **Modificação de horário do sistema**: o **bloco** impede que os usuários finais alterem as configurações de data e hora no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Os usuários podem alterar essas configurações.
    - **Modificação das configurações de região** (somente desktop): **Bloquear** impede que os usuários finais alterem as configurações de região no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Os usuários podem alterar essas configurações.
    - **Modificação das configurações de idioma (somente desktop)** : **Bloquear** impede que os usuários finais alterem as configurações de idioma no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Os usuários podem alterar essas configurações.

      [CSP de política de configurações](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Jogos**: **Bloquear** impede o acesso à área de jogos do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Facilidade de acesso**: **Bloquear** impede o acesso à área de facilidade de acesso do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Privacidade**: **Bloquear** impede o acesso à área de privacidade do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Update and Security**: **Block** impede o acesso à área de segurança de atualização & do aplicativo de configurações no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

## <a name="display"></a>Apresentar

Essas configurações usam o [CSP de política de vídeo](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display); que também lista as edições do Windows com suporte.

O dimensionamento de DPI GDI permite que aplicativos que não têm reconhecimento de DPI se tornem com reconhecimento de DPI por monitor.

- **Ativar o dimensionamento de GDI para aplicativos**: **adicione** os aplicativos herdados que você deseja que o DIMENSIONAmento de DPI GDI esteja ativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento de DPI GDI é ativado para todos os aplicativos herdados na sua lista.

- Desativar o **dimensionamento de GDI para aplicativos**: **adicione** os aplicativos herdados que você deseja que o dimensionamento de DPI GDI seja desativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento de DPI GDI é desativado para todos os aplicativos herdados na sua lista.

Você também pode **importar** um arquivo. csv com a lista de aplicativos.

## <a name="general"></a>Geral

Essas configurações usam o [CSP da política de experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience); que também lista as edições do Windows com suporte. 

- **Captura de tela** (somente dispositivos móveis): o **bloco** impede que os usuários finais obtenham capturas no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Copiar e colar (somente dispositivos móveis)** : o **bloco** impede que os usuários finais usem copiar e colar entre aplicativos no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Cancelamento de registro manual**: **Bloquear** impede que os usuários finais excluam a conta da empresa usando o painel de controle do local de trabalho no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

  Essa configuração de política não se aplicará se o computador for ingressado no Azure AD e o registro automático estiver habilitado.

- **Instalação manual de certificado raiz** (somente dispositivos móveis): o **bloqueio** impede que os usuários finais instalem manualmente certificados raiz e certificados de limite intermediários. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Camera**: **Bloquear** impede que os usuários finais usem a câmera no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

  [CSP da câmera](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-camera)

- **Sincronização de arquivos do onedrive**: o **bloco** impede que os usuários finais sincronizem arquivos no onedrive a partir do dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Armazenamento removível**: o **bloco** impede que os usuários finais usem dispositivos de armazenamento externo, como cartões SD com o dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Geolocalização**: **Bloquear** impede que os usuários finais ativem os serviços de localização no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Compartilhamento de Internet**: **Bloquear** impede o compartilhamento de conexão com a Internet no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Redefinição de telefone**: **Bloquear** impede que os usuários finais apagam ou façam uma redefinição de fábrica no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Conexão USB**: o **bloco** impede o acesso a dispositivos de armazenamento externo por meio de uma conexão USB no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. O carregamento de USB não é afetado por essa configuração.
- **Modo antifurto** (somente dispositivos móveis): o **bloco** impede que os usuários finais selecionem a preferência do modo antifurto no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Cortana**: **Bloquear** desabilita o assistente de voz Cortana no dispositivo. Quando a Cortana está desativada, os usuários ainda podem pesquisar para localizar itens no dispositivo. **Não configurado** (padrão) permite a Cortana.
- **Gravação de voz** (somente dispositivos móveis): o **bloco** impede que os usuários finais usem o gravador de voz do dispositivo no dispositivo. **Não configurado** (padrão) permite a gravação de voz para aplicativos.
- **Modificação do nome do dispositivo** (somente dispositivos móveis): o **bloco** impede que os usuários finais alterem o nome do dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Adicionar pacotes de provisionamento**: **Bloquear** impede o agente de configuração de tempo de execução que instala pacotes de provisionamento no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Remover pacotes de provisionamento**: **Bloquear** impede o agente de configuração de tempo de execução que remove pacotes de provisionamento do dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Descoberta de dispositivo**: o **bloco** impede que o dispositivo seja descoberto por outros dispositivos. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Alternador de tarefa** (somente dispositivos móveis): **Bloquear** impede a alternância de tarefas no dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Caixa de diálogo de erro do cartão Sim** (somente dispositivos móveis): **Bloquear** mensagens de erro de exibição no dispositivo se nenhum cartão Sim for detectado. **Não configurado** (padrão) mostra as mensagens de erro.
- **Espaço de trabalho de tinta**: escolha se e como o usuário acessa o espaço de trabalho de tinta. As opções são:
  - **Não configurado** (padrão): ativa o espaço de trabalho de tinta e o usuário tem permissão para usá-lo acima da tela de bloqueio.
  - **Desabilitado na tela de bloqueio**: o espaço de trabalho de tinta está habilitado e o recurso está ativado. No entanto, o usuário não pode acessá-lo acima da tela de bloqueio.
  - **Desabilitado**: o acesso ao espaço de trabalho de tinta está desabilitado. O recurso está desativado.

  [CSP de política do WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Reimplantação automática**: escolha **permitir** para que os usuários com direitos administrativos possam excluir todos os dados e configurações de usuário usando **Ctrl + Win + R** na tela de bloqueio do dispositivo. O dispositivo é reconfigurado automaticamente e registrado novamente no gerenciamento do. **Não configurado** (predefinição) impede esta funcionalidade.
- **Exigir que os usuários se conectem à rede durante a configuração do dispositivo**: escolha **exigir** para que o dispositivo se conecte a uma rede antes de passar pela página de rede durante a instalação do Windows. **Não configurado** (padrão) permite que os usuários passem pela página de rede, mesmo que não esteja conectado a uma rede.

  A configuração se tornará efetiva na próxima vez em que o dispositivo for apagado ou redefinido. Como qualquer outra configuração do Intune, o dispositivo deve ser registrado e gerenciado pelo Intune para receber as definições de configuração. Mas depois que ele é registrado e as políticas de recebimento, a redefinição do dispositivo impõe a configuração durante a próxima instalação do Windows.

  [CSP TenantLockdown](https://docs.microsoft.com/windows/client-management/mdm/tenantlockdown-csp)

- **Acesso direto à memória**: o **bloqueio** impede o acesso direto à memória (DMA) para todas as portas de downstream PCI conectadas a quente até que um usuário entre no Windows. **Habilitado** (padrão) permite o acesso ao DMA, mesmo quando um usuário não está conectado.

  [Dataprotection/CSP AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Encerrar processos do Gerenciador de tarefas**: essa configuração determina se não administradores podem usar o Gerenciador de tarefas para finalizar tarefas. **Bloquear** impede que usuários padrão (não administradores) usem o Gerenciador de tarefas para encerrar um processo ou uma tarefa no dispositivo. **Não configurado** (padrão) permite que usuários padrão encerrem um processo ou uma tarefa usando o Gerenciador de tarefas.

## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado

- **Notificações da central de ações (somente dispositivos móveis)** : **Bloquear** impede que as notificações da central de ações sejam exibidas na tela de bloqueio do dispositivo. **Não configurado** (padrão) permite que os usuários escolham quais aplicativos mostram as notificações na tela de bloqueio.

  [CSP AboveLock/AllowActionCenterNotifications](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#AboveLock_AllowActionCenterNotifications)

- **URL da imagem da tela bloqueada (somente desktop)** : Insira a URL para uma imagem no formato jpg, JPEG ou png que é usado como o papel de parede da tela de bloqueio do Windows. Por exemplo, introduza `https://contoso.com/image.png`. Essa configuração bloqueia a imagem e não pode ser alterada posteriormente.
- **Tempo limite de tela configurável pelo usuário (somente dispositivos móveis)** : **permitir** permite que os usuários configurem o tempo limite da tela. **Não configurado** (padrão) não dá aos usuários essa opção.

  [CSP DeviceLock/AllowScreenTimeoutWhileLockedUserConfig](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana na tela bloqueada** (somente desktop): o **bloco** impede que os usuários interajam com a Cortana quando o dispositivo está na tela de bloqueio. **Não configurado** (padrão) permite a interação com o Cortana.

  [CSP AboveLock/AllowCortanaAboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Notificações do sistema na tela bloqueada**: **Bloquear** impede que notificações do sistema sejam exibidas na tela de bloqueio do dispositivo. **Não configurado** (padrão) permite essas notificações.

  [CSP AboveLock/AllowToasts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Tempo limite da tela (somente dispositivos móveis)** : defina a duração (em segundos) da tela bloqueando a ativação da tela. Os valores com suporte são 11-1800. Por exemplo, digite `300` para definir esse tempo limite como 5 minutos.

  [CSP DeviceLock/ScreenTimeoutWhileLocked](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_ScreenTimeoutWhileLocked)

## <a name="messaging"></a>Mensagens

Essas configurações usam o [CSP de política de mensagens](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging); que também lista as edições do Windows com suporte.

- **Sincronização de mensagens (somente dispositivos móveis)** : o **bloco** desabilita a realização de backup e restauração de mensagens de texto e de sincronização de mensagens entre dispositivos Windows. Desabilitar ajuda a evitar que informações sejam armazenadas em servidores fora do controle da organização. **Não configurado** (padrão) permite que os usuários alterem essas configurações e sincronizem suas mensagens.
- **MMS (somente dispositivo móvel)** : o **bloco** desabilita a funcionalidade de envio e recebimento de MMS no dispositivo. Para empresas, use essa política para desabilitar o MMS em dispositivos como parte do requisito de gerenciamento ou auditoria. **Não configurado** (padrão) permite enviar e receber MMS.
- **RCS (somente dispositivos móveis)** : o **bloqueio** desabilita a funcionalidade de envio e recebimento de RCS (serviços de comunicação avançados) no dispositivo. Para empresas, use essa política para desabilitar o RCS nos dispositivos como parte do requisito de gerenciamento ou de auditoria. **Não configurado** (padrão) permite enviar e receber RCS.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

Essas configurações usam o [CSP da política do navegador](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), que também lista as edições do Windows com suporte.

### <a name="use-microsoft-edge-kiosk-mode"></a>Usar o modo de quiosque do Microsoft Edge

As configurações disponíveis são alteradas dependendo do que você escolher. As opções são:

- **Não** (padrão): o Microsoft Edge não está sendo executado no modo de quiosque. Todas as configurações do Microsoft Edge estão disponíveis para você alterar e configurar.
- **Pôsteres digitais/interativos (quiosque de aplicativo único)** : filtra as configurações do Microsoft Edge que são aplicáveis ao modo de quiosque digital/interativo de pôsteres do Microsoft Edge para uso somente em quiosques de aplicativo único do Windows 10. Escolha essa configuração para abrir uma tela inteira de URL e mostrar apenas o conteúdo nesse site. [Configurar sinais digitais](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fornece mais informações sobre esse recurso.
- **Navegação pública InPrivate (quiosque de aplicativo único)** : filtra as configurações do Microsoft Edge que são aplicáveis para a navegação pública inprivada modo de quiosque do Microsoft Edge para uso em quiosques de aplicativo único do Windows 10. Executa uma versão de várias guias do Microsoft Edge.
- **Modo normal (quiosque de vários aplicativos)** : filtra as configurações do Microsoft Edge que são aplicáveis para o modo de quiosque normal do Microsoft Edge. Executa uma versão completa do Microsoft Edge com todos os recursos de navegação.
- **Navegação pública (quiosque de vários aplicativos)** : filtra as configurações do Microsoft Edge que são aplicáveis para navegação pública em um quiosque de vários aplicativos do Windows 10.  Executa uma versão de várias guias do Microsoft Edge InPrivate.

> [!TIP]
> Para obter mais informações sobre o que essas opções fazem, consulte [tipos de configuração do modo de quiosque do Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Esse perfil de restrições de dispositivo está diretamente relacionado ao perfil de quiosque que você cria usando as [configurações de quiosque do Windows](kiosk-settings-windows.md). Resumindo:

1. Crie o perfil de [configurações de quiosque do Windows](kiosk-settings-windows.md) para executar o dispositivo no modo de quiosque. Selecione Microsoft Edge como o aplicativo e defina o modo de quiosque do Microsoft Edge no perfil de quiosque.
2. Crie o perfil de restrições de dispositivo descrito neste artigo e configure recursos específicos e configurações permitidas no Microsoft Edge. Certifique-se de escolher o mesmo tipo de modo de quiosque do Microsoft Edge, conforme selecionado no seu perfil de quiosque ([configurações de quiosque do Windows](kiosk-settings-windows.md)). 

    [As configurações de modo de quiosque com suporte](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) são um ótimo recurso.

> [!IMPORTANT] 
> Certifique-se de atribuir esse perfil do Microsoft Edge aos mesmos dispositivos que o seu perfil de quiosque ([configurações de quiosque do Windows](kiosk-settings-windows.md)).

[CSP ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Iniciar experiência

- **Iniciar o Microsoft Edge com**: escolha quais páginas são abertas quando o Microsoft Edge é iniciado. As opções são:
  - **Páginas iniciais personalizadas**: Insira as páginas iniciais, como `http://www.contoso.com`. O Microsoft Edge carrega as páginas iniciais que você inserir.
  - **Nova página de guia**: carregamento do Microsoft Edge, o que for inserido na nova configuração de **URL da guia** .
  - **Página da última sessão**: o Microsoft Edge carrega a página da última sessão.
  - **Iniciar páginas em configurações do aplicativo local**: Microsoft Edge iniciar com a página inicial padrão definida pelo sistema operacional.

- **Permitir que o usuário altere as páginas iniciais**: **Sim** (padrão) permite que os usuários alterem as páginas iniciais. Os administradores podem usar o `EdgeHomepageUrls` para inserir as páginas iniciais que os usuários veem por padrão ao abrir o Microsoft Edge. **Não** impede que os usuários alterem as páginas iniciais.
- **Permitir conteúdo da Web na nova página da guia**: quando definido como **Sim** (padrão), o Microsoft Edge abre a URL inserida na nova configuração de **URL da guia** . Se a **nova** configuração de URL da guia estiver em branco, o Microsoft Edge abrirá a nova página da guia listada em configurações do Microsoft Edge. Os usuários podem alterá-lo. Quando definido como **não**, o Microsoft Edge abre uma nova guia com uma página em branco. Os usuários não podem alterá-lo.
- **Nova URL de guia**: Insira a URL a ser aberta na página da nova guia. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.

- **Botão página inicial**: escolha o que acontece quando o botão página inicial é selecionado. As opções são:
  - **Páginas iniciais**: abre a opção escolhida na configuração **iniciar o Microsoft Edge com**
  - **Nova página de guia**: abre a URL que você inseriu na nova configuração de **URL de guia** .
  - **URL do botão página inicial**: Insira a URL a ser aberta. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.
  - **Ocultar botão página inicial**: oculta o botão página inicial
- **Permitir que os usuários alterem o botão Início**: **Sim** permite que os usuários alterem o botão página inicial. As alterações do usuário substituem as configurações do administrador no botão página inicial. **Não** (padrão) impede que os usuários alterem o modo como o administrador configurou o botão página inicial.
- **Mostrar página de experiência da primeira execução (somente dispositivo móvel)** : **Sim** (padrão) mostra a primeira página de introdução de uso no Microsoft Edge. **Não** impede que a página de introdução mostre a primeira vez que você executa o Microsoft Edge. Esse recurso permite que empresas, como organizações inscritas em zero configurações de emissões, bloqueiem essa página.
- **Local da lista de URLs de experiência da primeira execução** (somente Windows 10 Mobile): Insira a URL que aponta para o arquivo XML que contém as URLs de página da primeira execução. Por exemplo, introduza `https://www.contoso.com/sites.xml`.

- **Atualizar o navegador após o tempo ocioso**: Insira o número de minutos ociosos até que o navegador seja atualizado, de 0-1440 minutos. O padrão é `5` minutos. Quando definido como `0` (zero), o navegador não é atualizado depois de ficar ocioso.

  Essa configuração só está disponível quando executada na [navegação pública InPrivate (quiosque de aplicativo único)](#use-microsoft-edge-kiosk-mode).

- **Permitir pop-ups** (somente desktop): **Sim** (padrão) permite pop-ups no navegador da Web. **Não** impede janelas pop-up no navegador.
- **Enviar tráfego de intranet para o Internet Explorer** (somente desktop): **Sim** permite que os usuários abram sites de intranet no Internet Explorer em vez do Microsoft Edge. Essa configuração é para compatibilidade com versões anteriores. **Não** (padrão) permite que os usuários usem o Microsoft Edge.
- **Local da lista de sites do modo empresarial** (somente desktop): Insira a URL que aponta para o arquivo XML que contém uma lista de sites que são abertos no modo empresarial. Os usuários não podem alterar essa lista. Por exemplo, introduza `https://www.contoso.com/sites.xml`.
- **Mensagem ao abrir sites no Internet Explorer**: Use essa configuração para configurar o Microsoft Edge para mostrar uma notificação antes que um site seja aberto no Internet Explorer 11. As opções são:
  - **Não mostrar mensagem**: o comportamento padrão do sistema operacional é usado, o que pode não mostrar uma mensagem.
  - **Mostrar mensagem que o site está aberto no Internet Explorer 11**: mostrar a mensagem ao abrir sites no IE. Sites abertos no IE. 
  - **Mostrar mensagem com a opção de abrir sites no Microsoft Edge**: Mostre a mensagem ao abrir sites no Microsoft Edge. A mensagem inclui um link **continuar a usar o Microsoft Edge** para que os usuários possam escolher o Microsoft Edge em vez do IE.

  > [!IMPORTANT]
  > Essa configuração exige que você use a configuração **local da lista de sites do modo empresarial** , a configuração **enviar tráfego de intranet para o Internet Explorer** ou ambas as configurações.

- **Permitir lista de compatibilidade da Microsoft**: **Sim** (padrão) permite usar uma lista de compatibilidade da Microsoft. **Não** impede a lista de compatibilidade da Microsoft no Microsoft Edge. Esta lista da Microsoft ajuda o Microsoft Edge a exibir corretamente sites com problemas de compatibilidade conhecidos.
- **Pré-carregar páginas de início e nova página de guia**: **Sim** (padrão) usa o comportamento padrão do sistema operacional, que pode ser para pré-carregar essas páginas. O pré-carregamento minimiza o tempo para iniciar o Microsoft Edge e carrega novas guias. **Não** impede que o Microsoft Edge carregue páginas iniciais e a nova página da guia.
- **Páginas inicial de pré-inicialização e nova guia página**: **Sim** (padrão) usa o comportamento padrão do sistema operacional, que pode ser inicializar essas páginas. Iniciar previamente ajuda o desempenho do Microsoft Edge e minimiza o tempo necessário para iniciar o Microsoft Edge. **Não** impede o Microsoft Edge de inicializar previamente as páginas inicial e a nova guia.

### <a name="favorites-and-search"></a>Favoritos e pesquisa

- **Mostrar barra de favoritos**: escolha o que acontece com a barra de favoritos em qualquer página do Microsoft Edge. As opções são:
  - **Nas páginas inicial e nova guia**: mostra a barra favoritos quando o Microsoft Edge é iniciado e em todas as páginas da guia. Os usuários finais podem alterar essa configuração.
  - **Em todas as páginas**: mostra a barra de favoritos em todas as páginas. Os usuários finais não podem alterar essa configuração.
  - **Hidden**: oculta a barra de favoritos em todas as páginas. Os usuários finais não podem alterar essa configuração.
- **Permitir alterações em favoritos**: **Sim** (padrão) usa o padrão do sistema operacional, que permite aos usuários alterar a lista. **Não** impede que os usuários finais adicionem, importem, classifiquem ou editem a lista de favoritos.
  - **Lista de favoritos**: Adicione uma lista de URLs ao arquivo de favoritos. Por exemplo, adicione `http://contoso.com/favorites.html`.
- **Sincronizar favoritos entre os navegadores da Microsoft** (somente desktop): **Sim** força o Windows a sincronizar os favoritos entre o Internet Explorer e o Microsoft Edge. Adições, exclusões, modificações e alterações de pedidos a favoritos são compartilhadas entre navegadores.  **Não** (padrão) usa o padrão do sistema operacional, o que pode dar aos usuários a opção de sincronizar os favoritos entre os navegadores.
- **Mecanismo de pesquisa padrão**: escolha o mecanismo de pesquisa padrão no dispositivo. Os utilizadores finais podem alterar este valor em qualquer altura. As opções são:
  - Mecanismo de pesquisa nas configurações do Microsoft Edge do cliente
  - Bing
  - Google
  - Yahoo
  - Valor personalizado: na **URL XML de OpenSearch**, insira uma URL HTTPS com o arquivo XML que inclui o nome curto e a URL para o mecanismo de pesquisa, no mínimo. Por exemplo, introduza `https://www.contoso.com/opensearch.xml`.
- **Mostrar sugestões de pesquisa**: **Sim** (padrão) permite que o mecanismo de pesquisa sugira sites à medida que você digita frases de pesquisa na barra de endereços. **Não** impede esse recurso.
- **Permitir alterações no mecanismo de pesquisa**: **Sim** (padrão) permite que os usuários adicionem novos mecanismos de pesquisa ou altere o mecanismo de pesquisa padrão no Microsoft Edge. Escolha **não** para impedir que os usuários personalizem o mecanismo de pesquisa.

  Essa configuração só está disponível quando executada no [modo normal (quiosque de vários aplicativos)](#use-microsoft-edge-kiosk-mode).

### <a name="privacy-and-security"></a>Privacidade e segurança

- **Permitir navegação InPrivate**: **Sim** (padrão) permite navegação InPrivate no Microsoft Edge. Depois de fechar todas as guias InPrivate, o Microsoft Edge exclui os dados de navegação do dispositivo. **Não** impede que os usuários finais Abram sessões de navegação InPrivate.
- **Salvar histórico de navegação**: **Sim** (padrão) permitir salvar o histórico de navegação no Microsoft Edge. **Não** impede que o histórico de navegação seja salvo.
- **Limpar dados de navegação ao sair** (somente desktop): **Sim** limpa o histórico e procurando dados quando o usuário sai do Microsoft Edge. **Não** (padrão) usa o padrão do sistema operacional, que pode armazenar em cache os dados de navegação.
- **Sincronizar configurações do navegador entre dispositivos do usuário**: escolha como você deseja sincronizar as configurações do navegador entre os dispositivos. As opções são:
  - **Permitir**: permitir a sincronização das configurações do navegador Microsoft Edge entre os dispositivos do usuário
  - **Bloquear e habilitar substituição de usuário**: bloqueia a sincronização das configurações do navegador Microsoft Edge entre os dispositivos do usuário. Os usuários podem substituir essa configuração.
  - **Bloquear**: bloquear a sincronização da configuração do navegador Microsoft Edge entre os dispositivos dos usuários. Os usuários não podem substituir essa configuração.

Quando "bloquear e habilitar substituição de usuário" está selecionado, o usuário pode substituir a designação de administrador.

- **Permitir Gerenciador de senhas**: **Sim** (padrão) permite que o Microsoft Edge use automaticamente o Gerenciador de senhas, que permite que os usuários salvem e gerenciem senhas no dispositivo. **Não** impede que o Microsoft Edge use o Gerenciador de senhas.
- **Cookies**: escolha como os cookies são tratados no navegador da Web. As opções são:
  - **Permitir**: cookies são armazenados no dispositivo.
  - **Bloquear todos os cookies**: os cookies não são armazenados no dispositivo.
  - **Bloquear somente cookies**de terceiros: os cookies de terceiros ou parceiros não são armazenados no dispositivo.
- **Permitir preenchimento automático em formulários**: **Sim** (padrão) permite que os usuários alterem as configurações de preenchimento automático no navegador e populem campos de formulário automaticamente. **Não** desabilita o recurso de preenchimento automático no Microsoft Edge.
- **Enviar cabeçalhos do-não rastrear**: **Sim** envia cabeçalhos do not Track para sites solicitando informações de acompanhamento (recomendado). **Não** (padrão) não envia cabeçalhos, o que permite que sites acompanhem o usuário. O usuário pode configurar.
- **Mostrar endereço IP do localhost WebRTC**: **Sim** (padrão) permite que o endereço IP do localhost dos usuários seja mostrado ao fazer chamadas telefônicas usando esse protocolo. **Não** impede que o endereço IP do localhost dos usuários seja mostrado. 
- **Permitir coleta de dados de bloco dinâmico**: **Sim** (padrão) permite que o Microsoft Edge colete informações de blocos dinâmicos fixados no menu iniciar. **Não** impede a coleta dessas informações, o que pode fornecer aos usuários uma experiência limitada.
- O **usuário pode substituir erros de certificado**: **Sim** (padrão) permite que os usuários acessem sites que têm erros de protocolo SSL/TLS (segurança de camada de transporte). **Não** (recomendado para maior segurança) impede que os usuários acessem sites com erros SSL ou TLS.

### <a name="additional"></a>Adicionais

- **Permitir navegador Microsoft Edge** (somente dispositivos móveis): **Sim** (padrão) permite usar o navegador da Web Microsoft Edge no dispositivo móvel. **Não** impede o uso do Microsoft Edge no dispositivo. Se você escolher **não**, as outras configurações individuais se aplicarão somente ao desktop.
- **Permitir lista suspensa de barra de endereços**: **Sim** (padrão) permite que o Microsoft Edge mostre o menu suspenso da barra de endereços com uma lista de sugestões. **Não** impede o Microsoft Edge de mostrar uma lista de sugestões em uma lista suspensa quando você digita. Quando definido como **não**, você:
  - Ajude a minimizar a largura de banda de rede entre o Microsoft Edge e os serviços da Microsoft.
  - Desabilite a **exibição mostrar sugestões de pesquisa e site enquanto eu digitar** no Microsoft Edge > configurações.
- **Permitir modo de tela inteira**: **Sim** (padrão) permite que o Microsoft Edge use o modo de fullscreen, que mostra apenas o conteúdo da Web e oculta a interface do usuário do Microsoft Edge. **Não** impede o modo de tela inteira no Microsoft Edge.
- **Página permitir sobre sinalizadores**: **Sim** (padrão) usa o padrão do sistema operacional, que pode permitir o acesso à página de `about:flags`. A página `about:flags` permite que os usuários alterem as configurações do desenvolvedor e habilitem recursos experimentais. **Não** impede que os usuários finais acessem a página de `about:flags` no Microsoft Edge.
- **Permitir ferramentas de desenvolvedor**: **Sim** (padrão) permite que os usuários usem as ferramentas de desenvolvedor F12 para criar e depurar páginas da Web por padrão. **Não** impede que os usuários finais usem as ferramentas de desenvolvedor F12.
- **Permitir JavaScript**: **Sim** (padrão) permite que scripts, como JavaScript, sejam executados no navegador Microsoft Edge. **Não** impede a execução de scripts java no navegador.
- O **usuário pode instalar extensões**: **Sim** (padrão) permite que os usuários finais instalem extensões do Microsoft Edge no dispositivo. **Não** impede a instalação.
- **Permitir Sideload de extensões do desenvolvedor**: **Sim** (padrão) usa o padrão do sistema operacional, que pode permitir o Sideload. O Sideload instala e executa extensões não verificadas. **Não** impede o Microsoft Edge de Sideload usando o recurso de **extensões de carregamento** . Ele não impede extensões de Sideload usando outras maneiras, como o PowerShell.
- **Extensões necessárias**: escolha quais extensões não podem ser desativadas pelos usuários finais no Microsoft Edge. Insira os nomes da família de pacotes e selecione **Adicionar**. [Encontre um nome de família de pacotes (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) que fornece algumas diretrizes.

  Você também pode **importar** um arquivo CSV que inclui os nomes da família de pacotes. Ou então, **exporte** os nomes de família de pacotes que você inserir.

## <a name="network-proxy"></a>Proxy de rede

Essas configurações usam o [CSP da política do NetworkProxy](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), que também lista as edições do Windows com suporte.

- **Detectar automaticamente as configurações de proxy**: o **bloqueio** desabilita o dispositivo de detectar automaticamente um script PAC (configuração automática de proxy). **Não configurado** (padrão) habilita esse recurso. Quando habilitado, o dispositivo tenta localizar o caminho para um script PAC.
- **Usar script de proxy**: escolha **permitir** para inserir um caminho para o script de PAC para configurar o servidor proxy. **Não configurado** (padrão) não permite que você insira a URL para um script de PAC.
  - **URL do endereço do script de instalação**: Insira a URL de um script de PAC que você deseja usar para configurar o servidor proxy.
- **Usar servidor proxy manual**: escolha **permitir** para inserir manualmente o nome ou endereço IP e o número da porta TCP de um servidor proxy. **Não configurado** (padrão) não permite que você insira manualmente os detalhes de um servidor proxy.
  - **Endereço**: Insira o nome ou o endereço IP do servidor proxy.
  - **Número da porta**: Insira o número da porta do servidor proxy.
  - **Exceções de proxy**: Insira as URLs que não devem usar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
  - **Ignorar servidor proxy para endereço local**: **não configurado** (padrão) impede o uso de um servidor proxy para endereços locais na sua intranet. **Permitir** usa um servidor proxy para endereços locais.

## <a name="password"></a>Palavra-passe

Essas configurações usam o [CSP da política do DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), que também lista as edições do Windows com suporte.

- **Senha**: **exige** que o usuário final Insira uma senha para acessar o dispositivo. **Não configurado** (padrão) permite o acesso ao dispositivo sem uma senha. Aplica-se somente a contas locais. As senhas de conta de domínio permanecem configuradas pelo Active Directory (AD) e pelo Azure AD.

  - **Tipo de senha necessária**: escolha o tipo de senha. As opções são:
    - **Não configurado**: a senha pode incluir números e letras.
    - **Numeric**: a senha deve ser apenas números.
    - **Alfanumérico**: a senha deve ser uma combinação de números e letras.
  - **Comprimento mínimo da senha**: Insira o número mínimo ou os caracteres necessários, de 4-16. Por exemplo, digite `6` para exigir pelo menos seis caracteres no comprimento da senha.
  
    > [!IMPORTANT]
    > Quando o requisito de senha for alterado em uma área de trabalho do Windows, os usuários serão afetados na próxima vez que entrarem, como é quando o dispositivo vai de ocioso para ativo. Os usuários com senhas que atendem ao requisito ainda são solicitados a alterar suas senhas.
    
  - **Número de falhas de entrada antes de apagar o dispositivo**: Insira o número de falhas de autenticação permitidas antes que o dispositivo possa ser apagado, até 11. O número válido que você inserir dependerá da edição. O [CSP DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) lista os valores com suporte. `0` (zero) pode desabilitar a funcionalidade de apagamento do dispositivo.

    Essa configuração também tem um impacto diferente dependendo da edição. Para obter detalhes específicos sobre essa configuração, consulte o [CSP DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Máximo de minutos de inatividade até o bloqueio da tela**: Insira o período de tempo que um dispositivo deve ficar ocioso antes que a tela seja bloqueada.
  - **Expiração da senha (dias)** : Insira o período de tempo em dias em que a senha do dispositivo deve ser alterada, de 1-365. Por exemplo, digite `90` para expirar a senha após 90 dias.
  - **Evitar a reutilização de senhas anteriores**: Insira o número de senhas usadas anteriormente que não podem ser usadas, de 1-24. Por exemplo, digite `5` para que os usuários não possam definir uma nova senha para sua senha atual ou com qualquer uma de suas quatro senhas anteriores.
  - **Exigir senha quando o dispositivo retorna do estado ocioso** (móvel e Holographic): escolha **exigir** para que os usuários precisem inserir uma senha para desbloquear o dispositivo depois de ficar ocioso. **Não configurado** (padrão) não exige um PIN ou senha quando o dispositivo é retomado do estado ocioso.
  - **Senhas simples**: Defina como **Bloquear** para que os usuários não possam criar senhas simples, como `1234` ou `1111`. Defina como **não configurado** (padrão) para permitir que os usuários criem senhas como `1234` ou `1111`. Esta definição também permite ou bloqueia a utilização de palavras-passe por imagem do Windows.
- **Criptografia automática durante a AADJ**: o **bloqueio** impede a criptografia de dispositivo BitLocker automática quando o dispositivo está preparado para o primeiro uso, quando o dispositivo é ingressado no Azure AD. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Mais sobre a [criptografia de dispositivo do BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Segurança/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Política de padrão FIPS (FIPS)** : **permitir** usa a política de padrão FIPS (FIPS), que é um padrão do governo dos EUA para criptografia, hash e assinatura. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional não pode usar o FIPS.

  [CSP de criptografia/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticação de dispositivo do Windows Hello**: **permita que** os usuários usem um dispositivo complementar do Windows Hello, como um telefone, uma faixa de ADEQÜAÇÃO ou um dispositivo IOT, para entrar em um computador com Windows 10. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional pode impedir que dispositivos do Windows Hello Companion se autentiquem com o Windows.

  [Autenticação/CSP AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Entrada na Web**: habilita o suporte de entrada do Windows para provedores federados não ADFS (serviços de Federação do Active Directory (AD FS)), como Security ASSERTION MARKUP Language (SAML). O SAML usa tokens seguros que fornecem aos navegadores da Web uma experiência de logon único (SSO). As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Habilitado**: o provedor de credenciais da Web está habilitado para entrada.
  - **Desabilitado**: o provedor de credenciais da Web está desabilitado para entrar.

  [Autenticação/CSP EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Domínio de locatário do Azure ad preferencial**: Insira um nome de domínio existente na sua organização do Azure AD. Quando os usuários nesse domínio entram, eles não precisam digitar o nome de domínio. Por exemplo, introduza `contoso.com`. Os usuários no domínio `contoso.com` podem entrar usando seu nome de usuário, como `abby`, em vez de `abby@contoso.com`.

  [Autenticação/CSP PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>Exceções de privacidade por aplicação

Você pode adicionar aplicativos que devem ter um comportamento de privacidade diferente do que você define em "privacidade padrão".

- **Nome do pacote**: nome da família de pacotes de aplicativos.
- **Nome do aplicativo**: o nome do aplicativo.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se este aplicativo pode acessar o nome de usuário, a imagem e outras informações de contato.
- **Aplicativos em segundo plano**: Defina se este aplicativo pode ser executado em segundo plano.
- **Calendário**: Defina se este aplicativo pode acessar o calendário.
- **Histórico de chamadas**: Defina se este aplicativo pode acessar meu histórico de chamadas.
- **Câmera**: Defina se este aplicativo pode acessar a câmera.
- **Contatos**: Defina se este aplicativo pode acessar contatos.
- **Email**: Defina se este aplicativo pode acessar e enviar email.
- **Local**: Defina se este aplicativo pode acessar informações de local.
- **Mensagens**: Defina se este aplicativo pode ler ou enviar mensagens de texto ou MMS.
- **Microfone**: Defina se este aplicativo pode usar o microfone.
- **Movimento**: Defina se este aplicativo pode acessar informações de movimento do dispositivo.
- **Notificações**: Defina se este aplicativo pode acessar notificações.
- **Telefone**: Defina se este aplicativo pode acessar o telefone.
- **Rádios**: alguns aplicativos usam rádios (por exemplo, Bluetooth) em seu dispositivo para enviar e receber dados e precisam ativar ou desativar essas rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se este aplicativo pode acessar suas tarefas.
- **Dispositivos confiáveis**: escolha se este aplicativo pode usar dispositivos confiáveis. Os dispositivos confiáveis são o hardware que você já conectou ou o hardware que vem com o dispositivo. Por exemplo, use TVs, projetores e assim por diante, como dispositivos confiáveis.
- **Comentários e diagnóstico**: Defina se este aplicativo pode acessar informações de diagnóstico.
- **Sincronizar com dispositivos**: escolha se este aplicativo pode compartilhar e sincronizar informações automaticamente com dispositivos sem fio que não emparelham explicitamente com o dispositivo.

## <a name="personalization"></a>Personalização

Essas configurações usam o [CSP de política de personalização](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), que também lista as edições do Windows com suporte.

- **URL da imagem de fundo da área de trabalho (somente desktop)** : Insira a URL para uma imagem no formato. jpg,. jpeg ou. png que você deseja usar como papel de parede da área de trabalho do Windows. Os utilizadores não podem alterar a imagem. Por exemplo, introduza `https://contoso.com/logo.png`.

## <a name="printer"></a>Impressora

- **Impressoras**: lista de impressoras locais que foram adicionadas.
- **Impressora padrão**: defina a impressora padrão.
- **Acesso do usuário para adicionar novas impressoras**: permitir ou bloquear o uso de impressoras locais.

## <a name="privacy"></a>Privacidade

Essas configurações usam o [CSP de política de privacidade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), que também lista as edições do Windows com suporte.

- **Personalização de entrada**: **bloco** impede o uso de voz para ditado e para se comunicar com a Cortana e outros aplicativos que usam o reconhecimento de fala baseado em nuvem da Microsoft. Ele está desabilitado e os usuários não podem habilitar o reconhecimento de fala online usando as configurações. **Não configurado** (padrão) permite que os usuários escolham. Se você permitir esses serviços, a Microsoft poderá coletar dados de voz para melhorar o serviço.
- **Aceitação automática dos prompts de consentimento do usuário de privacidade e emparelhamento**: escolha **permitir** para que o Windows possa aceitar automaticamente as mensagens de consentimento de emparelhamento e privacidade ao executar aplicativos. **Não configurado** (padrão) impede a aceitação automática da janela de consentimento do usuário de privacidade e emparelhamento ao abrir aplicativos.
- **Publicar atividades do usuário**: **Bloquear** impede experiências compartilhadas e a descoberta de recursos usados recentemente no feed de atividades. **Não configurado** (padrão) habilita esse recurso para que os aplicativos possam publicar atividades do usuário final.
- **Somente atividades locais**: o **bloqueio** impede experiências compartilhadas e a descoberta de recursos usados recentemente no alternador de tarefas, com base apenas na atividade local. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

Você pode configurar informações que todos os aplicativos no dispositivo podem acessar. Além disso, defina exceções em uma base por aplicativo usando **exceções de privacidade por aplicativo**.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se este aplicativo pode acessar o nome de usuário, a imagem e outras informações de contato.
- **Aplicativos em segundo plano**: Defina se este aplicativo pode ser executado em segundo plano.
- **Calendário**: Defina se este aplicativo pode acessar o calendário.
- **Histórico de chamadas**: Defina se este aplicativo pode acessar meu histórico de chamadas.
- **Câmera**: Defina se este aplicativo pode acessar a câmera.
- **Contatos**: Defina se este aplicativo pode acessar contatos.
- **Email**: Defina se este aplicativo pode acessar e enviar email.
- **Local**: Defina se este aplicativo pode acessar informações de local.
- **Mensagens**: Defina se este aplicativo pode ler ou enviar mensagens de texto ou MMS.
- **Microfone**: Defina se este aplicativo pode usar o microfone.
- **Movimento**: Defina se este aplicativo pode acessar informações de movimento do dispositivo.
- **Notificações**: Defina se este aplicativo pode acessar notificações.
- **Telefone**: Defina se este aplicativo pode acessar o telefone.
- **Rádios**: alguns aplicativos usam rádios (por exemplo, Bluetooth) em seu dispositivo para enviar e receber dados e precisam ativar ou desativar essas rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se este aplicativo pode acessar suas tarefas.
- **Dispositivos confiáveis**: escolha se este aplicativo pode usar dispositivos confiáveis. Os dispositivos confiáveis são o hardware que você já conectou ou o hardware que acompanha o dispositivo. Por exemplo, use TVs, projetores e assim por diante, como dispositivos confiáveis.
- **Comentários e diagnóstico**: escolha se este aplicativo pode acessar informações de diagnóstico.
- **Sincronização com dispositivos** – defina se esta aplicação pode partilhar e sincronizar automaticamente informações com dispositivos sem fios que não sejam emparelhados especificamente com o PC, tablet ou telefone.

## <a name="projection"></a>Projeção

Essas configurações usam o [CSP da política do WirelessDisplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), que também lista as edições do Windows com suporte.

- **Entrada do usuário de receptores de exibição sem fio**: **Bloquear** impede a entrada do usuário de receptores de vídeo sem fio. **Não configurado** (padrão) permite que uma exibição sem fio envie teclado, mouse, caneta e entrada por toque de volta para o dispositivo de origem.
- **Projeção neste PC: o** **bloco** impede que outros dispositivos localizem o dispositivo para projeção. **Não configurado** (padrão) permite que o dispositivo seja detectável e pode projetar no dispositivo acima da tela de bloqueio.
- **Exigir PIN para emparelhamento**: escolha **exigir** para sempre solicitar um PIN ao se conectar a um dispositivo de projeção. **Não configurado** (padrão) não exige um PIN para emparelhar o dispositivo a um dispositivo de projeção.

## <a name="reporting-and-telemetry"></a>Relatórios e telemetria

- **Compartilhar dados de uso**: escolha o nível de dados de diagnóstico que é enviado. As opções são:
  - **Não configurado**: nenhum dado é compartilhado.
  - **Segurança**: informações necessárias para ajudar a manter o Windows mais seguro, incluindo dados sobre as configurações de componentes de telemetria e experiência do usuário conectado, a ferramenta de remoção de software mal-intencionado e o Microsoft defender.
  - **Básico**: informações básicas do dispositivo, incluindo dados relacionados à qualidade, compatibilidade de aplicativos, dados de uso do aplicativo e dados do nível de segurança.
  - **Aprimorado**: informações adicionais, incluindo: como o Windows, o Windows Server, o System Center e os aplicativos são usados, como eles executam, dados de confiabilidade avançados e dados dos níveis básico e de segurança.
  - **Completo**: todos os dados necessários para identificar e ajudar a corrigir problemas, além de dados dos níveis de segurança, básico e avançado.

  [CSP do sistema/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Enviar dados de navegação do Microsoft Edge para Microsoft 365 Analytics**: para usar esse recurso, defina as configurações de **dados de uso do compartilhamento** como **avançado** ou **completo**. Esse recurso controla quais dados o Microsoft Edge envia para Microsoft 365 análise para dispositivos empresariais com uma ID comercial configurada. As opções são:
  - **Não configurado**: o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional pode não enviar nenhum dado de histórico de navegação.
  - **Somente enviar dados da intranet**: permite que o administrador envie o histórico de dados da intranet
  - **Somente enviar dados da Internet**: permite que o administrador envie o histórico de dados da Internet
  - **Enviar dados da intranet e da Internet**: permite que o administrador envie o histórico de dados da intranet e da Internet

  [CSP do navegador/ConfigureTelemetryForMicrosoft365Analytics](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Servidor proxy de telemetria**: Insira o FQDN (nome de domínio totalmente qualificado) ou o endereço IP de um servidor proxy para encaminhar as experiências de usuário conectadas e as solicitações de telemetria usando uma conexão protocolo SSL (SSL). O formato para esta definição é *servidor*:*porta*. Se o proxy nomeado falhar ou se um proxy não for inserido ao habilitar essa política, os dados de experiência de usuário conectados e telemetria não serão enviados e permanecerão no dispositivo local.

  Formatos de exemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [CSP do sistema/TelemetryProxy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Selecione **OK** para guardar as alterações.

## <a name="search"></a>Procura

Essas configurações usam o [CSP de política de pesquisa](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), que também lista as edições do Windows com suporte. 

- **Pesquisa segura (somente dispositivos móveis)** : controle como a Cortana filtra conteúdo adulto nos resultados da pesquisa. As opções são:
  - **Definido pelo usuário**: permitir que os usuários finais escolham suas próprias configurações.
  - **Estrito**: filtragem mais alta contra conteúdo adulto.
  - **Moderado**: filtragem moderada contra conteúdo adulto. Os resultados de pesquisa válidos não são filtrados.
- **Exibir resultados da Web na pesquisa**: quando definido como **Bloquear**, os usuários não podem pesquisar e os resultados da Web não são mostrados na pesquisa. **Não configurado** (padrão) permite que os usuários pesquisem a Web e os resultados sejam mostrados no dispositivo.

## <a name="start"></a>Iniciar,

Essas configurações usam o [CSP de política inicial](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), que também lista as edições do Windows com suporte.  

- **Layout do menu iniciar**: substitua o layout de início padrão e personalize o menu iniciar em dispositivos de desktop. Carregue um arquivo XML que inclui suas personalizações, incluindo a ordem em que os aplicativos são listados e muito mais. Os usuários não podem alterar o layout do menu iniciar inserido.
- **Fixe sites a blocos no menu iniciar**: importe imagens do Microsoft Edge que são mostradas como links no menu Iniciar do Windows para dispositivos de desktop.
- **Desafixar aplicativos da barra de tarefas**: o **bloco** impede que os usuários desafixam aplicativos da barra de tarefas. **Não configurado** (padrão) permite que os usuários desafixem aplicativos da barra de tarefas.
- **Troca rápida de usuário**: **Bloquear** impede a troca de usuários que estão conectados simultaneamente sem fazer logoff. **Não configurado** (padrão) mostra o **usuário do comutador** no bloco do usuário.
- **Aplicativos mais usados**: o **bloco** oculta a exibição dos aplicativos mais usados no menu iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os aplicativos mais usados.
- **Aplicativos adicionados recentemente**: **Bloquear** oculta aplicativos adicionados recentemente da exibição no menu iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os aplicativos adicionados recentemente no menu iniciar.
- **Modo de tela inicial**: escolha como a tela inicial é mostrada. As opções são:
  - **Definido pelo usuário**: não força o tamanho do início. Os usuários podem definir o tamanho.
  - **Tela inteira**: força um tamanho de tela inicial.
  - **Tela não completa**: força o tamanho de não-tela inicial.
- **Itens abertos recentemente nas listas de atalhos**: **Bloquear** oculta as listas de atalhos recentes de serem mostradas no menu iniciar e na barra de tarefas. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os itens abertos recentemente no atalhos.
- **Lista de aplicativos**: escolha como as listas todos os aplicativos são mostradas. As opções são:
  - **Definido pelo usuário**: nenhuma configuração é forçada. Os usuários escolhem como a lista de aplicativos é mostrada no dispositivo.
  - **Recolher**: ocultar a lista todos os aplicativos.
  - **Recolha e desabilite a lista configurações aplicativo**: Ocultar todos os aplicativos e desabilite **Mostrar lista de aplicativos no menu iniciar** no aplicativo configurações.
  - **Remove e desabilita o botão configurações aplicativo**: Ocultar todos os aplicativos, remover todos os aplicativos e desabilitar **Mostrar lista de aplicativos no menu iniciar** no aplicativo configurações.
- **Botão de energia**: **Bloquear** oculta o botão de energia da exibição no menu iniciar. **Não configurado** (padrão) mostra o botão de energia.
- **Bloco do usuário**: o **bloco** oculta a exibição do bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra o bloco do usuário e também define as seguintes configurações:
  - **Bloquear**: **Bloquear** oculta a opção de **bloqueio** da exibição no bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra a opção de **bloqueio** .
  - **Sair**: **Bloquear** oculta a opção **sair** da exibição no bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra a opção de **sair** .
- **Desligar**: **Bloquear** oculta as opções de **atualização e** desligamento e **desligamento** da exibição no botão de energia no menu iniciar. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Sleep**: o **bloco** oculta a opção de **suspensão** da exibição no botão de energia no menu iniciar. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Hibernar**: **Bloquear** oculta a opção **hibernar** da exibição no botão de energia no menu iniciar. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Alternar conta**: o **bloco** oculta a **conta do comutador** da exibição no bloco do usuário no menu iniciar. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Opções de reinicialização**: o **bloco** oculta as opções de **atualização e reinicialização** e **reinicialização** de mostrar no botão de energia no menu iniciar. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
- **Documentos em Iniciar**: oculta ou mostra a pasta documentos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Downloads em Iniciar**: oculta ou mostra a pasta de downloads no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Explorador de arquivos em Iniciar**: oculta ou mostra o explorador de arquivos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Grupo doméstico em Iniciar**: oculta ou mostra o atalho do grupo doméstico no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Música em Iniciar**: oculte ou mostre a pasta música no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Rede ao iniciar**: ocultar ou mostrar entrada na rede menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Pasta pessoal em Iniciar**: ocultar ou mostrar a pasta pessoal no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Imagens em Iniciar**: oculte ou mostre a pasta para imagens no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Configurações em Iniciar**: oculta ou mostra o atalho configurações no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Vídeos em Iniciar**: oculta ou mostra a pasta para vídeos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (padrão): nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: o atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: o atalho é mostrado e desabilita a configuração no aplicativo configurações.

## <a name="microsoft-defender-smart-screen"></a>Tela inteligente do Microsoft defender

- **SmartScreen para Microsoft Edge**: **requer** a desativação do Microsoft defender SmartScreen e impede que os usuários o liguem. **Não configurado** (padrão) ativa o SmartScreen. Ajuda a proteger os usuários contra possíveis ameaças e impede que os usuários o desativem.

  O Microsoft Edge usa o Microsoft defender SmartScreen (ativado) para proteger os usuários contra possíveis golpes de phishing e software mal-intencionado.

  [CSP do navegador/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Acesso de site mal-intencionado**: o **bloqueio** impede que os usuários ignorem os avisos do filtro do Microsoft defender SmartScreen e os bloqueia de ir para o site. **Não configurado** (padrão) permite que os usuários ignorem os avisos e continuem no site.

  [CSP do navegador/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Download de arquivo não verificado**: o **bloco** impede que os usuários ignorem os avisos de filtro do Microsoft defender SmartScreen e os bloqueiam do download de arquivos não verificados. **Não configurado** (padrão) permite que os usuários ignorem os avisos e continuem a baixar os arquivos não verificados.

  [CSP do navegador/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Destaque do Windows

Essas configurações usam o [CSP da política de experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), que também lista as edições do Windows com suporte.

- **Destaque do Windows**: o **bloco** desativa o destaque do Windows na tela de bloqueio, dicas do Windows, recursos de consumidor da Microsoft e outros recursos relacionados. Se seu objetivo é minimizar o tráfego de rede dos dispositivos, defina-o como **Bloquear**. **Não configurado** (padrão) permite recursos de destaque do Windows e pode ser controlado por usuários finais. Quando habilitado, você também pode permitir ou bloquear as seguintes configurações:

  - **Destaque do Windows na tela de bloqueio**: **Bloquear** impede que o destaque do Windows exiba informações na tela de bloqueio do dispositivo. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Sugestões de terceiros no Windows Spotlight**: **Bloquear** impede o destaque do Windows de sugerir conteúdo que não é publicado pela Microsoft. **Não configurado** (padrão) permite sugestões de aplicativos e conteúdo de Publicadores de software de parceiros em recursos de destaque do Windows, como o destaque da tela de bloqueio, aplicativos sugeridos no menu iniciar e dicas do Windows.
  - **Recursos do consumidor**: **bloco** desativa as experiências que normalmente são apenas para consumidores, como sugestões de início, notificações de associação, instalação do aplicativo de experiência de lançamento e blocos de redirecionamento. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.
  - **Dicas do Windows**: **Bloquear** desabilita dicas pop-up do Windows. **Não configurado** (padrão) permite que as dicas do Windows sejam exibidas.
  - **Destaque do Windows na central de ações**: **Bloquear** impede que notificações de destaque do Windows sejam exibidas na central de ações. **Não configurado** (padrão) pode mostrar notificações na central de ações que sugerem aplicativos ou recursos para ajudar os usuários a serem mais produtivos no Windows.
  - **Personalização de destaque do Windows**: **Bloquear** impede que o Windows use dados de diagnóstico para fornecer experiências personalizadas ao usuário. **Não configurado** (padrão) permite que a Microsoft use dados de diagnóstico para fornecer recomendações, dicas e ofertas personalizadas para personalizar o Windows para as necessidades do usuário.
  - **Experiência de boas-vindas do Windows**: o **bloqueio** desativa o recurso de experiência do Windows Welcome do Windows. A experiência de boas-vindas do Windows não mostrará quando houver atualizações e alterações no Windows e em seus aplicativos. **Não configurado** (padrão) permite que a experiência de boas-vindas do Windows mostre as informações do usuário sobre os recursos novos ou atualizados.

## <a name="microsoft-defender-antivirus"></a>Microsoft defender antivírus

Essas configurações usam o [CSP de política do defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), que também lista as edições do Windows com suporte.

- **Monitoramento em tempo real**: **habilitar** ativa a verificação em tempo real para malware, spyware e outros softwares indesejados. Os usuários não podem desativá-lo. 

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa esse recurso e permite que os usuários o alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **Monitoramento de comportamento**: **habilitar** ativa o monitoramento de comportamento e verifica determinados padrões conhecidos de atividade suspeita em dispositivos. Os usuários não podem desativar o monitoramento de comportamento. 

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa o monitoramento de comportamento e permite que os usuários o alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **Sistema de inspeção de rede (NIS)** : o NIS ajuda a proteger dispositivos contra explorações baseadas em rede. Utiliza as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e bloquear tráfego malicioso.

  **Habilitar** ativa a proteção de rede e o bloqueio de rede. Os usuários não podem desativá-lo. Quando habilitado, os usuários são impedidos de se conectar a vulnerabilidades conhecidas.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa o NIS e permite que os usuários o alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **Verificar todos os downloads**: **habilitar** ativa essa configuração e o defender examina todos os arquivos baixados da Internet. Os usuários não podem desativar essa configuração. 

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa essa configuração e permite que os usuários a alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **Verificar scripts carregados nos navegadores da Web da Microsoft**: **habilitar** permite que o defender examine scripts que são usados no Internet Explorer. Os usuários não podem desativar essa configuração. 

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa essa configuração e permite que os usuários a alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- O **acesso do usuário final ao defender**: **Block** oculta a interface do usuário do Microsoft defender dos usuários finais. Todas as notificações do Microsoft defender também são suprimidas.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você bloquear a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional permite que o usuário acesse a IU do Microsoft defender e permite que os usuários o alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  Quando esta definição for alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.

  [CSP do defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **Intervalo de atualização de inteligência de segurança (em horas)** : Insira o intervalo que o defender verifica para obter uma nova inteligência de segurança, de 0-24. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional pode verificar se há atualizações a cada 8 horas.
  - Não **verificar**: o defender não verifica se há novas atualizações de inteligência de segurança.
  - **1-24**: `1` verifica a cada hora, `2` verifica a cada duas horas, `24` verifica todos os dias e assim por diante.
  
  [CSP do defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **Monitorar a atividade de arquivos e programas**: permite que o defender monitore a atividade de arquivos e programas nos dispositivos. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional pode monitorar todos os arquivos.
  - **Monitoramento desabilitado**
  - **Monitorar todos os arquivos**
  - **Monitorar somente arquivos recebidos**
  - **Monitorar somente arquivos de saída**

  [CSP do defender/RealTimeScanDirection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **Dias antes da exclusão de malware em quarentena**: Continue acompanhando o malware resolvido pelo número de dias que você inseriu para que você possa verificar manualmente os dispositivos afetados anteriormente. Se você definir o número de dias para `0`, o malware permanecerá na pasta de quarentena e não será removido automaticamente. Quando definido como `90`, os itens de quarentena são armazenados por 90 dias no sistema e, em seguida, removidos.

  [CSP do defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **Limite de uso da CPU durante uma verificação**: limite a quantidade de CPU que as verificações têm permissão para usar, de `0` para `100`.
- **Verificar arquivos mortos**: **habilitar** ativa o defender para que ele examine arquivos mortos, como arquivos zip ou cab. Os usuários não podem desativar essa configuração.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa essa verificação e permite que os usuários a alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **Examinar mensagens de email recebidas**: **habilitar** permite que o defender Verifique mensagens de email à medida que elas chegam no dispositivo. Quando habilitado, o mecanismo analisa os arquivos de caixa de correio e de email para analisar o corpo e os anexos dos emails. Você pode verificar os formatos. pst (Outlook),. dbx,. MBX, MIME (Outlook Express) e BinHex (Mac).

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional desativa essa verificação e permite que os usuários a alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **Verificar unidades removíveis durante uma verificação completa**: **habilitar** ativa as verificações da unidade removível do defender durante uma verificação completa. Os usuários não podem desativar essa configuração.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional permite que o defender Verifique unidades removíveis, como pentes USB, e permite que os usuários alterem essa configuração.

  Durante uma verificação rápida, as unidades removíveis ainda podem ser verificadas.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **Verificar unidades de rede mapeadas durante uma verificação completa**: **habilitar** tem arquivos de verificação do defender em unidades de rede mapeadas. Se os arquivos na unidade forem somente leitura, o defender não poderá remover nenhum malware encontrado neles. Os usuários não podem desativar essa configuração.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional ativa esse recurso e permite que os usuários o alterem.

  Durante uma verificação rápida, as unidades de rede mapeadas ainda podem ser verificadas.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **Verificar arquivos abertos de pastas de rede**: **habilitar** tem o defender verifica arquivos abertos de pastas de rede ou unidades de rede compartilhadas, como arquivos acessados de um caminho UNC. Os usuários não podem desativar essa configuração. Se os arquivos na unidade forem somente leitura, o defender não poderá remover nenhum malware encontrado neles.

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional verifica os arquivos abertos das pastas de rede e permite que os usuários o alterem.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **Proteção de nuvem**: **habilitar** ativa o Microsoft Active Protection Service para receber informações sobre a atividade de malware de dispositivos que você gerencia. Os usuários não podem alterar essa configuração. 

  Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração. Se você habilitar a configuração e, em seguida, alterá-la novamente para **não configurado**, o Intune deixará a configuração no estado configurado anteriormente. Por padrão, o sistema operacional permite que o Microsoft Active Protection Service receba informações e permite que os usuários alterem essa configuração.

  O Intune não desativa esse recurso. Para desabilitá-lo, use um URI personalizado.

  [CSP do defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **Avisar os usuários antes do envio de exemplo**: controla se arquivos potencialmente mal-intencionados que podem exigir análise adicional são enviados automaticamente à Microsoft. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração. O padrão do sistema operacional pode enviar amostras seguras automaticamente.
  - **Sempre avisar**
  - **Avisar antes de enviar dados pessoais**
  - **Nunca enviar dados**
  - **Enviar todos os dados sem avisar**: os dados são enviados automaticamente.

  [CSP do defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **Tempo para executar uma verificação rápida diária**: escolha a hora para executar uma verificação rápida diária. **Não configurado** não executa uma verificação diária. Se você quiser mais personalização, configure o **tipo de verificação do sistema para executar** a configuração.

  [CSP do defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Tipo de verificação do sistema a ser executada**: agendar uma verificação do sistema, incluindo o nível de verificação e o dia e hora para executar a verificação. As opções são:
  - **Não configurado**: não agenda uma verificação do sistema no dispositivo. Os usuários finais podem executar verificações manualmente conforme necessário ou desejados em seus dispositivos.
  - **Desabilitar**: desabilita qualquer verificação do sistema no dispositivo. Escolha esta opção se você estiver usando uma solução antivírus de parceiro que verifica os dispositivos.
  - **Verificação rápida**: examina locais comuns em que pode haver malware registrado, como chaves do registro e pastas de inicialização conhecidas do Windows.
    - **Dia agendado**: escolha o dia para executar a verificação.
    - **Hora agendada**: escolha a hora para executar a verificação.
  - **Verificação completa**: examina os locais comuns onde pode haver malware registrado e examina todos os arquivos e pastas no dispositivo.
    - **Dia agendado**: escolha o dia para executar a verificação.
    - **Hora agendada**: escolha a hora para executar a verificação.

  > [!TIP]
  > Essa configuração pode entrar em conflito com o **tempo para executar uma configuração de verificação rápida diária** . Algumas recomendações:  
  >
  > - Se você quiser agendar uma verificação rápida diária e uma verificação completa semanal, então:
  >   1. Configure o **tempo para executar uma configuração de verificação rápida diária** .
  >   2. Configure o **tipo de verificação do sistema a ser executado para realizar** uma verificação completa.
  > 
  > - Se você quiser apenas uma verificação rápida diária (sem verificação completa), use qualquer uma das configurações: **tempo para executar uma verificação rápida diária** ou **tipo de verificação do sistema a ser executada**. Por exemplo, para executar uma verificação rápida toda terça-feira às 18h, configure o **tipo de verificação do sistema para executar** a configuração.
  > 
  > - Não configure o **tempo para executar uma configuração de verificação rápida diária** simultaneamente com o **tipo de verificação do sistema para executar** a **verificação rápida**. Essas configurações podem entrar em conflito e uma verificação pode não ser executada.

  [CSP do defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP do defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP do defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Detectar aplicativos potencialmente indesejados**: escolha o nível de proteção quando o Windows detecta aplicativos potencialmente indesejados. As opções são:
  - **Não configurado** (padrão): a proteção de aplicativos potencialmente indesejados do Microsoft defender está desabilitada.
  - **Bloquear**: o Microsoft defender detecta aplicativos potencialmente indesejados e os itens detectados são bloqueados. Esses itens são mostrados em histórico junto com outras ameaças.
  - **Auditoria**: o Microsoft defender detecta aplicativos potencialmente indesejados, mas não realiza nenhuma ação. Você pode examinar as informações sobre os aplicativos que o Microsoft defender tomaria em ação. Por exemplo, pesquise eventos criados pelo Microsoft defender na Visualizador de Eventos.

  Para obter mais informações sobre aplicativos potencialmente indesejados, consulte [detectar e bloquear aplicativos potencialmente indesejados](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

  [CSP do defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **Ações sobre ameaças de malware detectadas**: escolha como você deseja tratar os threads de malware. **Não configurado** (padrão) permite que o Microsoft defender escolha a melhor opção. Quando definido como **habilitar**, escolha as ações que você deseja que o defender assuma para cada nível de ameaça que detectar: baixa, moderada, alta e grave. As opções são:
  
  - **Limpar**
  - **Quarentena**
  - **Remove**
  - **Permitir**
  - **Definido pelo utilizador**
  - **Bloquear**

  Se a ação não for possível, o Microsoft defender escolherá a melhor opção para garantir que a ameaça seja corrigida. 

  [CSP do defender/ThreatSeverityDefaultAction](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="microsoft-defender-antivirus-exclusions"></a>Exclusões do Microsoft defender antivírus

- **Arquivos e pastas a serem excluídos das verificações e da proteção em tempo real**: Adiciona um ou mais arquivos e pastas como **C:\Path** ou **%ProgramFiles%\Path\filename.exe** à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
- **Extensões de arquivo a serem excluídas de verificações e proteção em tempo real**: Adicione uma ou mais extensões de arquivo, como **jpg** ou **txt** , à lista de exclusões. Todos os arquivos com essas extensões não são incluídos em verificações em tempo real ou programadas.
- **Processos a serem excluídos de verificações e proteção em tempo real**: Adicione um ou mais processos do tipo **. exe**, **. com**ou **. scr** à lista de exclusões. Esses processos não estão incluídos em verificações em tempo real ou programadas.

## <a name="power-settings"></a>Definições de energia

### <a name="battery"></a>Bateria

- **Nível da bateria para ativar a economia de energia**: quando o dispositivo estiver usando energia da bateria, insira o nível de carga da bateria para ativar a economia de energia de 0-100. Insira um valor percentual que indica o nível de carga da bateria. O valor padrão é 70%. Quando definido como 70%, a economia de energia é ativada quando a bateria tem 70% de encargo ou menos disponível.

  [CSP de energia/EnergySaverBatteryThresholdOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdonbattery)

- **Fechamento da tampa (somente dispositivos móveis)** : quando o dispositivo estiver usando energia da bateria, escolha o que acontece quando a tampa é fechada. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado e continua a usar a energia da bateria.
  - **Suspensão**: o dispositivo entra no modo de suspensão e usa uma pequena quantidade de carga de bateria. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.

  [CSP de energia/SelectLidCloseActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactiononbattery)

- **Botão de energia**: quando o dispositivo estiver usando energia da bateria, escolha o que acontece quando o botão de energia é selecionado. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado e continua a usar a energia da bateria.
  - **Suspensão**: o dispositivo entra no modo de suspensão e usa uma pequena quantidade de carga de bateria. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.

  [CSP de energia/SelectPowerButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactiononbattery)

- **Botão de suspensão**: quando o dispositivo estiver usando energia da bateria, escolha o que acontece quando o botão de suspensão é selecionado. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado e continua a usar a energia da bateria.
  - **Suspensão**: o dispositivo entra no modo de suspensão e usa uma pequena quantidade de carga de bateria. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.

  [CSP de energia/SelectSleepButtonActionOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactiononbattery)

- **Suspensão híbrida**: quando o dispositivo estiver usando energia da bateria, **desabilitar** impedirá que o dispositivo vá para o modo de suspensão híbrida. No modo de suspensão híbrida, os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório) e no disco rígido. Ele usa uma pequena quantidade de carga de bateria. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

  [CSP de energia/TurnOffHybridSleepOnBattery](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeponbattery)

### <a name="pluggedin"></a>PluggedIn

- **Nível da bateria para ativar a economia de energia**: quando o dispositivo estiver conectado, insira o nível de carga da bateria para ativar a economia de energia de 0-100. Insira um valor percentual que indica o nível de carga da bateria. O valor padrão é 70%. Quando definido como 70%, a economia de energia é ativada quando a bateria tem 70% de encargo ou menos disponível.

  [CSP de energia/EnergySaverBatteryThresholdPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-energysaverbatterythresholdpluggedin)

- **Fechamento da tampa (somente dispositivos móveis)** : quando o dispositivo estiver conectado, escolha o que acontece quando a tampa é fechada. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado.
  - **Suspensão**: o dispositivo entra no modo de suspensão. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.
  
    [CSP de energia/SelectLidCloseActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectlidcloseactionpluggedin)
  
- **Botão de energia**: quando o dispositivo estiver conectado, escolha o que acontece quando o botão de energia é selecionado. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado.
  - **Suspensão**: o dispositivo entra no modo de suspensão. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.

  [CSP de energia/SelectPowerButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectpowerbuttonactionpluggedin)

- **Botão de suspensão**: quando o dispositivo estiver conectado, escolha o que acontece quando o botão de suspensão é selecionado. As opções são:

  - **Não configurado** (padrão): o Intune não altera nem atualiza essa configuração.
  - **Nenhuma ação**: o dispositivo permanece ligado.
  - **Suspensão**: o dispositivo entra no modo de suspensão. O computador ainda está ativado e os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório).
  - **Hibernar**: o dispositivo entra no modo de hibernação. Os aplicativos abertos e os arquivos são armazenados no disco rígido e o dispositivo é desligado.
  - **Desligar**: o dispositivo é desligado. Os aplicativos e arquivos abertos são fechados sem salvar.

  [CSP de energia/SelectSleepButtonActionPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-selectsleepbuttonactionpluggedin)

- **Suspensão híbrida**: quando o dispositivo está conectado, **desabilite** impede que o dispositivo vá para o modo de suspensão híbrida. No modo de suspensão híbrida, os aplicativos e arquivos abertos são armazenados na RAM (memória de acesso aleatório) e no disco rígido. Quando definido como **não configurado** (padrão), o Intune não altera nem atualiza essa configuração.

  [CSP de energia/TurnOffHybridSleepPluggedIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power#power-turnoffhybridsleeppluggedin)

## <a name="next-steps"></a>Próximos passos

Para obter os detalhes técnicos adicionais de cada definição e quais as edições do Windows suportadas, veja [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referência de CSP de Políticas do Windows 10)
