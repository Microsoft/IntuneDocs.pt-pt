---
title: Definições de restrição de dispositivos para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Consulte uma lista de todas as configurações e suas descrições para criar restrições de dispositivo em dispositivos Windows 10 e posteriores. Use essas configurações em um perfil de configuração para controlar capturas de tela, requisitos de senha, configurações de quiosque, aplicativos na loja, navegador Microsoft Edge, Windows Defender, acesso à nuvem, menu iniciar e muito mais em Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b3fd474e938e2e85a0a08951a9e3f154d980411
ms.sourcegitcommit: b64869b4be357c0741ec01b1a2f0bae13efce937
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69998951"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Configurações do dispositivo Windows 10 (e mais recente) para permitir ou restringir recursos usando o Intune

Este artigo lista e descreve todas as diferentes configurações que você pode controlar em dispositivos Windows 10 e mais recentes. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, definir regras de senha, personalizar a tela de bloqueio, usar o Windows Defender e muito mais.

Essas configurações são adicionadas a um perfil de configuração de dispositivo no Intune e, em seguida, atribuídas ou implantadas em seus dispositivos Windows 10.

> [!Note]
> Nem todas as opções estão disponíveis em todas as edições do Windows. Para ver as edições com suporte, consulte os [CSPs da política](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (abre outro site da Microsoft).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

Essas configurações usam o [CSP da política do ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), que também lista as edições do Windows com suporte.

- **Loja de aplicativos** (somente dispositivos móveis): **Não configurado** (padrão) permite que os usuários finais acessem a loja de aplicativos em dispositivos móveis. **Bloquear** impede o uso da loja de aplicativos.
- **Atualizar automaticamente os aplicativos da loja**: **Não configurado** (padrão) permite que os aplicativos instalados do Microsoft Store sejam atualizados automaticamente. **Bloquear** impede que as atualizações sejam instaladas automaticamente.
- **Instalação de aplicativo confiável**: Escolha se os aplicativos não Microsoft Store podem ser instalados, também conhecidos como Sideload. O Sideload está sendo instalado e, em seguida, executando ou testando um aplicativo que não é certificado pelo Microsoft Store. Por exemplo, um aplicativo que é interno somente à sua empresa. As opções são:
  - **Não configurado** (predefinição): Usa o padrão do sistema operacional.
  - **Bloquear**: Impede o Sideload. Não é possível instalar aplicativos não Microsoft Store.
  - **Permitir**: Permite Sideload. Os aplicativos não Microsoft Store podem ser instalados.
- **Desbloqueio do desenvolvedor**: Permitir configurações de desenvolvedor do Windows, como permitir que aplicativos Sideload sejam modificados pelos usuários finais. As opções são:
  - **Não configurado** (predefinição): Usa o padrão do sistema operacional.
  - **Bloquear**: Impede o modo de desenvolvedor e aplicativos de Sideload.
  - **Permitir**: Permite o modo de desenvolvedor e aplicativos de Sideload.

  [Habilitar seu dispositivo para desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) tem mais informações sobre esse recurso.

- **Dados do aplicativo de usuário compartilhado**: Escolha **permitir** para compartilhar dados de aplicativo entre diferentes usuários no mesmo dispositivo e com outras instâncias desse aplicativo. **Não configurado** (padrão) impede o compartilhamento de dados com outros usuários e outras instâncias do mesmo aplicativo.
- **Usar somente o repositório particular**: **Permitir** que apenas os aplicativos sejam baixados de um armazenamento particular e não baixados do armazenamento público, incluindo um catálogo de varejo. **Não configurado** (padrão) permite que os aplicativos sejam baixados de um repositório particular e de um repositório público.
- **Inicialização do aplicativo originado no repositório**: **Bloquear** desabilita todos os aplicativos que foram pré-instalados no dispositivo ou baixados do Microsoft Store. **Não configurado** (padrão) permite que esses aplicativos sejam abertos.
- **Instalar dados de aplicativo no volume do sistema**: **Bloquear** impede que os aplicativos armazenem dados no volume do sistema do dispositivo. **Não configurado** (padrão) permite que os aplicativos armazenem dados no volume de disco do sistema.
- **Instalar aplicativos na unidade do sistema**: **Bloquear** impede que os aplicativos sejam instalados na unidade do sistema no dispositivo. **Não configurado** (padrão) permite que os aplicativos sejam instalados na unidade do sistema.
- **DVR de jogos** (somente desktop): **Bloquear** desabilita a gravação e a transmissão de jogos do Windows. **Não configurado** (padrão) permite a gravação e a difusão de jogos.
- **Aplicativos somente da loja**: Essa configuração determina a experiência do usuário quando os usuários instalam aplicativos de locais diferentes do Microsoft Store. As opções são:

  - **Não configurado** (predefinição): Permite que os usuários finais instalem aplicativos de locais diferentes do Microsoft Store, incluindo aplicativos definidos em outras configurações de política.  
  - **Em qualquer lugar**: Desativa as recomendações do aplicativo e permite que os usuários instalem aplicativos de qualquer local.  
  - **Somente armazenar**: Força os usuários finais a instalar somente aplicativos do Microsoft Store.
  - **Recomendações**: Ao instalar um aplicativo da Web que está disponível no Microsoft Store, os usuários veem uma mensagem recomendando que eles o baixem da loja.  
  - **Preferir armazenamento**: Avisa os usuários quando eles instalam aplicativos de locais diferentes do Microsoft Store.

  [CSP do SmartScreen/EnableAppInstallControl](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Controle do usuário sobre instalações**: Quando definido como **não configurado** (padrão), Windows Installer impedir que os usuários alterem as opções de instalação normalmente reservadas para administradores do sistema, como inserir o diretório para instalar os arquivos. **Bloquear** permite que os usuários alterem essas opções de instalação e alguns dos recursos de segurança de Windows Installer são ignorados.

  [CSP ApplicationManagement/MSIAllowUserControlOverInstall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Instalar aplicativos com privilégios elevados**: Quando definido como **não configurado** (padrão), o sistema aplica as permissões do usuário atual quando instala programas que um administrador do sistema não implanta ou oferece. O **bloco** instrui Windows Installer a usar permissões elevadas ao instalar qualquer programa no sistema. Esses privilégios são estendidos para todos os programas.

  [CSP ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Aplicativos de inicialização**: Insira uma lista de aplicativos a serem abertos depois que um usuário entrar no dispositivo. Certifique-se de usar uma lista delimitada por ponto-e-vírgula de nomes de família de pacotes (PFN) de aplicativos do Windows. Para que essa política funcione, o manifesto nos aplicativos do Windows deve usar uma tarefa de inicialização.

  [CSP ApplicationManagement/LaunchAppAfterLogOn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

Selecione **OK** para guardar as alterações.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

Essas configurações usam a [política de conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) e os CSPs da [política de Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) , que também listam as edições do Windows com suporte.

- [CSP da política Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Canal de dados da rede celular**: Escolha se os usuários finais podem usar dados, como navegar na Web, quando conectados a uma rede de celular. As opções são:
  - **Não configurado** (predefinição): Usa o padrão do sistema operacional, que pode permitir o canal de dados da rede celular. Os usuários finais podem desativá-lo.
  - **Bloquear**: Não permitir o canal de dados da rede celular. Os usuários finais não podem ativá-lo.
  - **Permitir (não editável)** : Permite o canal de dados da rede celular. Os usuários finais não podem desativá-lo.

- **Roaming de dados**: **Bloquear** impede o roaming de dados de celular no dispositivo. **Não configurado** (padrão) permite o roaming entre redes ao acessar dados.
- **VPN pela rede celular**: **Bloquear** impede que o dispositivo acesse conexões VPN quando conectado a uma rede de celular. **Não configurado** (padrão) permite que a VPN use qualquer conexão, incluindo a rede celular.
- **Roaming de VPN na rede celular**: **Bloquear** impede que o dispositivo acesse conexões VPN durante o roaming em uma rede de celular. **Não configurado** (padrão) permite conexões VPN quando em roaming.
- **Serviço de dispositivos conectados**: **Bloquear** desabilita o componente de CDP (plataforma de dispositivos conectados). A CDP permite a descoberta e a conexão com outros dispositivos (por meio de Bluetooth/LAN ou nuvem) para dar suporte à inicialização de aplicativos remotos, mensagens remotas, sessões de aplicativos remotos e outras experiências entre dispositivos. **Não configurado** (padrão) permite que o serviço dispositivos conectados, que permite a descoberta e a conexão com outros dispositivos Bluetooth.
- **NFC**: **Bloquear** impede recursos de comunicação a curta distância (NFC). **Não configurado** (padrão) permite que os usuários habilitem e configurem recursos de NFC no dispositivo.
- **Wi-Fi**: **Bloquear** impede que os usuários habilitem, configurem e usem conexões Wi-Fi no dispositivo. **Não configurado** (padrão) permite conexões Wi-Fi.
- **Conectar-se automaticamente a hotspots Wi-Fi**: **Bloquear** impede que os dispositivos se conectem automaticamente a hotspots Wi-Fi. **Não configurado** (padrão) permite que os dispositivos se conectem automaticamente a hotspots Wi-Fi gratuitos e aceitem automaticamente quaisquer termos e condições para a conexão.
- **Configuração manual de Wi-Fi**: **Bloquear** impede que os dispositivos se conectem ao Wi-Fi fora das redes instaladas pelo servidor MDM. **Não configurado** (padrão) permite que os usuários finais adicionem e configurem seus próprios SSIDs de rede de conexões Wi-Fi.
- **Intervalo de verificação de Wi-Fi**: Insira com que frequência os dispositivos verificam redes Wi-Fi. Insira um valor de 1 (mais frequente) a 500 (menos frequente). O padrão `0` é (zero).

### <a name="bluetooth"></a>Bluetooth

Essas configurações usam o [CSP de política do Bluetooth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth); que também lista as edições do Windows com suporte.

- **Bluetooth**: **Bloquear** impede que os usuários habilitem o Bluetooth. **Não configurado** (padrão) permite Bluetooth no dispositivo.
- **Descoberta de Bluetooth**: **Bloquear** impede que o dispositivo seja detectável por outros dispositivos habilitados para Bluetooth. **Não configurado** (padrão) permite que outros dispositivos habilitados para Bluetooth, como um headset, descubram o dispositivo.
- **Pré-emparelhamento Bluetooth**: **Bloquear** impede que dispositivos Bluetooth específicos Emparelhem automaticamente com um dispositivo de host. **Não configurado** (padrão) permite o emparelhamento automático com o dispositivo de host.
- **Publicidade de Bluetooth**: **Bloquear** impede que o dispositivo envie anúncios de Bluetooth. **Não configurado** (padrão) permite que o dispositivo envie anúncios de Bluetooth.
- **Serviços Bluetooth permitidos**: **Adicione** uma lista de perfis e serviços Bluetooth permitidos como cadeias de caracteres hexadecimais `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`, como.

  O [Guia de uso do ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) tem mais informações sobre a lista de serviços.

Selecione **OK** para guardar as alterações.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

Essas configurações usam o [CSP de política de contas](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts); que também lista as edições do Windows com suporte.

- **Conta Microsoft**: **Bloquear** impede que os usuários finais associem um conta Microsoft ao dispositivo. **Não configurado** (padrão) permite adicionar e usar um conta Microsoft.
- **Não conta Microsoft**: **Bloquear** impede que os usuários finais adicionem contas que não sejam da Microsoft usando a interface do usuário. **Não configurado** (padrão) permite que os usuários adicionem contas de email que não estão associadas a um conta Microsoft.
- **Sincronização de configurações para conta Microsoft**: **Não configurado** (padrão) permite que as configurações de dispositivo e aplicativo associadas a um conta Microsoft sincronizem entre dispositivos. **Bloquear** impede esta sincronização.
- **Assistente de conexão de conta da Microsoft**: Quando definido como **não configurado** (padrão), os usuários finais podem iniciar e parar o serviço do **Assistente de conexão de conta da Microsoft** (WLIDSVC). Esse serviço de sistema operacional permite que os usuários entrem em seus conta Microsoft. **Desabilitar** impede que os usuários finais controlem o serviço de assistente de conexão da Microsoft (WLIDSVC).

Selecione **OK** para guardar as alterações.

## <a name="cloud-printer"></a>Impressora em Cloud

Essas configurações usam o [CSP da política do EnterpriseCloudPrint](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint); que também lista as edições do Windows com suporte.

- **URL de descoberta de impressora**: Insira a URL para localizar impressoras de nuvem. Por exemplo, introduza `https://cloudprinterdiscovery.contoso.com`.
- **URL da autoridade de acesso à impressora**: Insira a URL de ponto de extremidade de autenticação para obter tokens OAuth. Por exemplo, introduza `https://azuretenant.contoso.com/adfs`.
- **GUID do aplicativo cliente nativo do Azure**: Insira o GUID de um aplicativo cliente com permissão para obter tokens OAuth do OAuthAuthority. Por exemplo, introduza `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI do recurso do serviço de impressão**: Insira o URI de recurso do OAuth para o serviço de impressão configurado no portal do Azure. Por exemplo, introduza `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Máximo de impressoras a serem consultadas**: Insira o número máximo de impressoras que você deseja consultar. O valor predefinido é `20`.
- **URI do recurso do serviço de descoberta de impressora**: Insira o URI de recurso do OAuth para o serviço de descoberta de impressora configurado no portal do Azure. Por exemplo, introduza `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Depois de configurar uma [impressão em nuvem híbrida do Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), você pode definir essas configurações e, em seguida, implantar em seus dispositivos Windows.

Selecione **OK** para guardar as alterações.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Aplicativo de configurações**: **Bloquear** impede que os usuários finais acessem o aplicativo de configurações do Windows. **Não configurado** (padrão) permite que os usuários abram o aplicativo configurações no dispositivo.
  - **Sistema**: **Bloquear** impede o acesso à área do sistema do aplicativo de configurações. **Não configurado** (padrão) permite o acesso.
    - **Modificação das configurações de energia e suspensão** (somente desktop): **Bloquear** impede que os usuários finais alterem as configurações de energia e suspensão no dispositivo. **Não configurado** (padrão) permite que os usuários alterem as configurações de energia e suspensão.
  - **Dispositivos**: **Bloquear** impede o acesso à área de dispositivos do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Internet de rede**: **Bloquear** impede o acesso à rede & área da Internet do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Personalização**: **Bloquear** impede o acesso à área de personalização do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Aplicações**: **Bloquear** impede o acesso à área de aplicativos do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Contas**: **Bloquear** impede o acesso à área contas do aplicativo configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Hora e idioma**: **Bloquear** impede o acesso ao horário & área de linguagem do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
    - **Modificação do horário do sistema**: **Bloquear** impede que os usuários finais alterem as configurações de data e hora no dispositivo. **Não configurado** permite que os usuários alterem essas configurações.
    - **Modificação das configurações de região** (somente desktop): **Bloquear** impede que os usuários finais alterem as configurações de região no dispositivo. **Não configurado** permite que os usuários alterem essas configurações.
    - **Modificação das configurações de idioma (somente desktop)** : **Bloquear** impede que os usuários finais alterem as configurações de idioma no dispositivo. **Não configurado** permite que os usuários alterem essas configurações.

      [CSP de política de configurações](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Jogos**: **Bloquear** impede o acesso à área de jogos do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Facilidade de acesso**: **Bloquear** impede o acesso à área de facilidade de acesso do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Privacidade**: **Bloquear** impede o acesso à área de privacidade do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.
  - **Atualização e segurança**: **Bloquear** impede o acesso à área de segurança & atualização do aplicativo de configurações no dispositivo. **Não configurado** (padrão) permite o acesso.

Selecione **OK** para guardar as alterações.

## <a name="display"></a>Apresentar

Essas configurações usam o [CSP de política de vídeo](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display); que também lista as edições do Windows com suporte.

O dimensionamento de DPI GDI permite que aplicativos que não têm reconhecimento de DPI se tornem com reconhecimento de DPI por monitor.

- **Ativar o dimensionamento de GDI para aplicativos**: **Adicione** os aplicativos herdados que você deseja que o dimensionamento de DPI GDI esteja ativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento de DPI GDI é ativado para todos os aplicativos herdados na sua lista.

- Desligar o **dimensionamento GDI para aplicativos**: **Adicione** os aplicativos herdados que você deseja que o dimensionamento de DPI GDI seja desativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento de DPI GDI é desativado para todos os aplicativos herdados na sua lista.

Você também pode **importar** um arquivo. csv com a lista de aplicativos.

Selecione **OK** para guardar as alterações.

## <a name="general"></a>Geral

Essas configurações usam o [CSP da política de experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience); que também lista as edições do Windows com suporte. 

- **Captura de tela** (somente dispositivos móveis): **Bloquear** impede que os usuários finais obtenham capturas de tela no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Copiar e colar (somente dispositivos móveis)** : **Bloquear** impede que os usuários finais usem copiar e colar entre aplicativos no dispositivo. **Não configurado** (padrão) permite esse recurso.
- Cancelamento de **registro manual**: **Bloquear** impede que os usuários finais excluam a conta do local de trabalho usando o painel de controle do local de trabalho no dispositivo. **Não configurado** (padrão) permite esse recurso.

  Essa configuração de política não se aplicará se o computador for ingressado no Azure AD e o registro automático estiver habilitado.

- **Instalação manual de certificado raiz** (somente dispositivos móveis): **Bloquear** impede que os usuários finais instalem manualmente certificados raiz e certificados de limite intermediários. **Não configurado** (padrão) permite esse recurso.
- **Câmara**: **Bloquear** impede que os usuários finais usem a câmera no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Sincronização de arquivos do onedrive**: **Bloquear** impede que os usuários finais sincronizem arquivos com o onedrive a partir do dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Armazenamento removível**: **Bloquear** impede que os usuários finais usem dispositivos de armazenamento externo, como cartões SD com o dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Localização geográfica**: **Bloquear** impede que os usuários finais ativem os serviços de localização no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Compartilhamento de Internet**: **Bloquear** impede o compartilhamento de conexão com a Internet no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Redefinição de telefone**: **Bloquear** impede que os usuários finais apagam ou façam uma redefinição de fábrica no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Conexão USB**: **Bloquear** impede o acesso a dispositivos de armazenamento externo por meio de uma conexão USB no dispositivo. **Não configurado** (padrão) permite esse recurso. O carregamento de USB não é afetado por essa configuração.
- **Modo antifurto** (somente dispositivos móveis): **Bloquear** impede que os usuários finais selecionem a preferência do modo antifurto no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Cortana**: **Bloquear** desabilitação do assistente de voz Cortana no dispositivo. Quando a Cortana está desativada, os usuários ainda podem pesquisar para localizar itens no dispositivo. **Não configurado** (padrão) permite a Cortana.
- **Gravação de voz** (somente dispositivos móveis): **Bloquear** impede que os usuários finais usem o gravador de voz do dispositivo no dispositivo. **Não configurado** (padrão) permite a gravação de voz para aplicativos.
- **Modificação do nome do dispositivo** (somente dispositivos móveis): **Bloquear** impede que os usuários finais alterem o nome do dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Adicionar pacotes de provisionamento**: **Bloquear** impede o agente de configuração de tempo de execução que instala pacotes de provisionamento no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Remover pacotes de provisionamento**: **Bloquear** impede o agente de configuração de tempo de execução que remove pacotes de provisionamento do dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Descoberta de dispositivo**: **Bloquear** impede que o dispositivo seja descoberto por outros dispositivos. **Não configurado** (padrão) permite esse recurso.
- **Alternador de tarefa** (somente dispositivos móveis): **Bloquear** impede a alternância de tarefas no dispositivo. **Não configurado** (padrão) permite esse recurso.
- **Diálogo de erro do cartão Sim** (somente dispositivos móveis): **Bloquear** mensagens de erro de serem exibidas no dispositivo se nenhum cartão Sim for detectado. **Não configurado** (padrão) mostra as mensagens de erro.
- **Espaço de trabalho de tinta**: Escolha se e como o usuário acessa o espaço de trabalho de tinta. As opções são:
  - **Não configurado** (predefinição): Ativa o espaço de trabalho de tinta e o usuário tem permissão para usá-lo acima da tela de bloqueio.
  - **Desabilitado na tela de bloqueio**: O espaço de trabalho de tinta está habilitado e o recurso está ativado. No entanto, o usuário não pode acessá-lo acima da tela de bloqueio.
  - **Desativado**: O acesso ao espaço de trabalho de tinta está desabilitado. O recurso está desativado.

  [CSP de política do WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Reimplantação automática**: Escolha **permitir** para que os usuários com direitos administrativos possam excluir todos os dados e configurações do usuário usando **Ctrl + Win + R** na tela de bloqueio do dispositivo. O dispositivo é reconfigurado automaticamente e registrado novamente no gerenciamento do. **Não configurado** (predefinição) impede esta funcionalidade.
- **Exigir que os usuários se conectem à rede durante a instalação do dispositivo**: Escolha **exigir** para que o dispositivo se conecte a uma rede antes de passar pela página de rede durante a instalação do Windows. **Não configurado** (padrão) permite que os usuários passem pela página de rede, mesmo que não esteja conectado a uma rede.

  A configuração se tornará efetiva na próxima vez em que o dispositivo for apagado ou redefinido. Como qualquer outra configuração do Intune, o dispositivo deve ser registrado e gerenciado pelo Intune para receber as definições de configuração. Mas depois que ele é registrado e as políticas de recebimento, a redefinição do dispositivo impõe a configuração durante a próxima instalação do Windows.

- **Acesso direto à memória**: O **bloqueio** impede o acesso direto à memória (DMA) para todas as portas de downstream PCI conectadas a quente até que um usuário entre no Windows. **Habilitado** (padrão) permite o acesso ao DMA, mesmo quando um usuário não está conectado.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Encerrar processos do Gerenciador de tarefas**: Essa configuração determina se não administradores podem usar o Gerenciador de tarefas para finalizar tarefas. **Bloquear** impede que usuários padrão (não administradores) usem o Gerenciador de tarefas para encerrar um processo ou uma tarefa no dispositivo. **Não configurado** (padrão) permite que usuários padrão encerrem um processo ou uma tarefa usando o Gerenciador de tarefas.

Selecione **OK** para guardar as alterações.

## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado

- **Notificações da central de ações (somente dispositivos móveis)** : **Bloquear** impede que as notificações da central de ações sejam exibidas na tela de bloqueio do dispositivo. **Não configurado** (padrão) permite que os usuários escolham quais aplicativos mostram notificações na tela de bloqueio.

  [CSP AboveLock/AllowActionCenterNotifications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **URL da imagem da tela bloqueada (somente desktop)** : Insira a URL para uma imagem no formato JPG, JPEG ou PNG que é usado como o papel de parede da tela de bloqueio do Windows. Por exemplo, introduza `https://contoso.com/image.png`. Essa configuração bloqueia a imagem e não pode ser alterada posteriormente.
- **Tempo limite de tela configurável pelo usuário (somente dispositivos móveis)** : **Permitir** permite que os usuários configurem o tempo limite da tela. **Não configurado** (padrão) não dá aos usuários essa opção.

  [CSP DeviceLock/AllowScreenTimeoutWhileLockedUserConfig](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **Cortana na tela bloqueada** (somente desktop): **Bloquear** impede que os usuários interajam com o Cortana quando o dispositivo está na tela de bloqueio. **Não configurado** (padrão) permite a interação com o Cortana.

  [CSP AboveLock/AllowCortanaAboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Notificações do sistema na tela bloqueada**: **Bloquear** impede que notificações do sistema sejam exibidas na tela de bloqueio do dispositivo. **Não configurado** (padrão) permite essas notificações.

  [CSP AboveLock/AllowToasts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Tempo limite da tela (somente dispositivos móveis)** : Defina a duração (em segundos) da tela bloqueando a ativação da tela. Os valores com suporte são 11-1800. Por exemplo, digite `300` para definir esse tempo limite como 5 minutos.

  [CSP DeviceLock/ScreenTimeoutWhileLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

Selecione **OK** para guardar as alterações.

## <a name="messaging"></a>Mensagens

Essas configurações usam o [CSP de política de mensagens](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging); que também lista as edições do Windows com suporte.

- **Sincronização de mensagens (somente dispositivos móveis)** : **Bloquear** desabilita o backup e a restauração de mensagens de texto e a sincronização de mensagens entre dispositivos Windows. Desabilitar ajuda a evitar que informações sejam armazenadas em servidores fora do controle da organização. **Não configurado** (padrão) permite que os usuários alterem essas configurações e sincronizem suas mensagens.
- **MMS (somente dispositivo móvel)** : **Bloquear** desabilita a funcionalidade de envio e recebimento de MMS no dispositivo. Para empresas, use essa política para desabilitar o MMS em dispositivos como parte do requisito de gerenciamento ou auditoria. **Não configurado** (padrão) permite enviar e receber MMS.
- **RCS (somente dispositivos móveis)** : **Bloquear** desabilita a funcionalidade de envio e recebimento de RCS (serviços de comunicação avançados) no dispositivo. Para empresas, use essa política para desabilitar o RCS nos dispositivos como parte do requisito de gerenciamento ou de auditoria. **Não configurado** (padrão) permite enviar e receber RCS.

Selecione **OK** para guardar as alterações.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

Essas configurações usam o [CSP da política do navegador](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), que também lista as edições do Windows com suporte.

### <a name="use-microsoft-edge-kiosk-mode"></a>Usar o modo de quiosque do Microsoft Edge

As configurações disponíveis são alteradas dependendo do que você escolher. As opções são:

- **Não** (padrão): O Microsoft Edge não está sendo executado no modo de quiosque. Todas as configurações do Microsoft Edge estão disponíveis para você alterar e configurar.
- **Pôsteres digitais/interativos (quiosque de aplicativo único)** : Filtra as configurações do Microsoft Edge que são aplicáveis para o modo de quiosque digital/interativo do Microsoft Edge para uso somente em quiosques de aplicativo único do Windows 10. Escolha essa configuração para abrir uma tela inteira de URL e mostrar apenas o conteúdo nesse site. [Configurar sinais digitais](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fornece mais informações sobre esse recurso.
- **Navegação não privada pública (quiosque de aplicativo único)** : Filtra as configurações do Microsoft Edge que são aplicáveis para a navegação pública inprivada modo de quiosque do Microsoft Edge para uso em quiosques de aplicativo único do Windows 10. Executa uma versão de várias guias do Microsoft Edge.
- **Modo normal (quiosque de vários aplicativos)** : Filtra as configurações do Microsoft Edge que são aplicáveis para o modo de quiosque normal do Microsoft Edge. Executa uma versão completa do Microsoft Edge com todos os recursos de navegação.
- **Navegação pública (quiosque de vários aplicativos)** : Filtra as configurações do Microsoft Edge que são aplicáveis para navegação pública em um quiosque de vários aplicativos do Windows 10.  Executa uma versão de várias guias do Microsoft Edge InPrivate.

> [!TIP]
> Para obter mais informações sobre o que essas opções fazem, consulte [tipos de configuração do modo de quiosque do Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Esse perfil de restrições de dispositivo está diretamente relacionado ao perfil de quiosque que você cria usando as [configurações de quiosque do Windows](kiosk-settings-windows.md). Para resumir:

1. Crie o perfil de [configurações de quiosque do Windows](kiosk-settings-windows.md) para executar o dispositivo no modo de quiosque. Selecione Microsoft Edge como o aplicativo e defina o modo de quiosque do Microsoft Edge no perfil de quiosque.
2. Crie o perfil de restrições de dispositivo descrito neste artigo e configure recursos específicos e configurações permitidas no Microsoft Edge. Certifique-se de escolher o mesmo tipo de modo de quiosque do Microsoft Edge, conforme selecionado no seu perfil de quiosque ([configurações de quiosque do Windows](kiosk-settings-windows.md)). 

    [As configurações de modo de quiosque com suporte](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) são um ótimo recurso.

> [!IMPORTANT] 
> Certifique-se de atribuir esse perfil do Microsoft Edge aos mesmos dispositivos que o seu perfil de quiosque ([configurações de quiosque do Windows](kiosk-settings-windows.md)).

[CSP ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Iniciar experiência

- **Inicie o Microsoft Edge com**: Escolha quais páginas são abertas quando o Microsoft Edge é iniciado. As opções são:
  - **Páginas de início personalizadas**: Insira as páginas iniciais, `http://www.contoso.com`como. O Microsoft Edge carrega as páginas iniciais que você inserir.
  - **Nova página de guia**: Carregamento do Microsoft Edge, o que for inserido na nova configuração de **URL da guia** .
  - **Página da última sessão**: O Microsoft Edge carrega a última página da sessão.
  - **Iniciar páginas em configurações do aplicativo local**: O Microsoft Edge começa com a página inicial padrão definida pelo sistema operacional.

- **Permitir que o usuário altere as páginas iniciais**: **Sim** (padrão) permite que os usuários alterem as páginas iniciais. Os administradores podem usar `EdgeHomepageUrls` o para inserir as páginas iniciais que os usuários veem por padrão ao abrir o Microsoft Edge. **Não** impede que os usuários alterem as páginas iniciais.
- **Permitir conteúdo da Web na nova página da guia**: Quando definido como **Sim** (padrão), o Microsoft Edge abre a URL inserida na nova configuração de **URL de guia** . Se a **nova** configuração de URL da guia estiver em branco, o Microsoft Edge abrirá a nova página da guia listada em configurações do Microsoft Edge. Os usuários podem alterá-lo. Quando definido como **não**, o Microsoft Edge abre uma nova guia com uma página em branco. Os usuários não podem alterá-lo.
- **Nova URL de guia**: Insira a URL a ser aberta na página da nova guia. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.

- **Botão página inicial**: Escolha o que acontece quando o botão página inicial está selecionado. As opções são:
  - **Páginas iniciais**: Abre a opção que você escolheu na configuração **iniciar o Microsoft Edge com**
  - **Nova página de guia**: Abre a URL que você inseriu na nova configuração de **URL de guia** .
  - **URL do botão página inicial**: Insira a URL a ser aberta. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.
  - **Ocultar botão página inicial**: Oculta o botão página inicial
- **Permitir que os usuários alterem o botão Início**: **Sim** permite que os usuários alterem o botão página inicial. As alterações do usuário substituem as configurações do administrador no botão página inicial. **Não** (padrão) impede que os usuários alterem o modo como o administrador configurou o botão página inicial.
- **Mostrar página de experiência da primeira execução (somente dispositivos móveis)** : **Sim** (padrão) mostra a primeira página de introdução de uso no Microsoft Edge. **Não** impede que a página de introdução mostre a primeira vez que você executa o Microsoft Edge. Esse recurso permite que empresas, como organizações inscritas em zero configurações de emissões, bloqueiem essa página.
- **Local da lista de URLs de experiência da primeira execução** (Somente Windows 10 Mobile): Insira a URL que aponta para o arquivo XML que contém as URLs da primeira página de execução. Por exemplo, introduza `https://www.contoso.com/sites.xml`.

- **Atualizar o navegador após o tempo ocioso**: Insira o número de minutos ociosos até que o navegador seja atualizado, de 0-1440 minutos. O padrão `5` é minutos. Quando definido como `0` (zero), o navegador não é atualizado depois de ficar ocioso.

  Essa configuração só está disponível quando executada na [navegação pública InPrivate (quiosque de aplicativo único)](#use-microsoft-edge-kiosk-mode).

- **Permitir pop-ups** (somente desktop): **Sim** (padrão) permite pop-ups no navegador da Web. **Não** impede janelas pop-up no navegador.
- **Enviar tráfego de intranet para o Internet Explorer** (Somente desktop): **Sim** permite que os usuários abram sites da intranet no Internet Explorer em vez do Microsoft Edge. Essa configuração é para compatibilidade com versões anteriores. **Não** (padrão) permite que os usuários usem o Microsoft Edge.
- **Local da lista de sites do modo empresarial** (Somente desktop): Insira a URL que aponta para o arquivo XML que contém uma lista de sites da Web que são abertos no modo empresarial. Os usuários não podem alterar essa lista. Por exemplo, introduza `https://www.contoso.com/sites.xml`.
- **Mensagem ao abrir sites no Internet Explorer**: Use essa configuração para configurar o Microsoft Edge para mostrar uma notificação antes que um site seja aberto no Internet Explorer 11. As opções são:
  - **Não mostrar mensagem**: O comportamento padrão do sistema operacional é usado, o que pode não mostrar uma mensagem.
  - **Mostrar mensagem que o site está aberto no Internet Explorer 11**: Mostre a mensagem ao abrir sites no IE. Sites abertos no IE. 
  - **Mostrar mensagem com a opção de abrir sites no Microsoft Edge**: Mostrar a mensagem ao abrir sites no Edge. A mensagem inclui um link **continuar a usar o Microsoft Edge** para que os usuários possam escolher o Microsoft Edge em vez do IE.

  > [!IMPORTANT]
  > Essa configuração exige que você use a configuração **local da lista de sites do modo empresarial** , a configuração **enviar tráfego de intranet para o Internet Explorer** ou ambas as configurações.

- **Permitir lista de compatibilidade da Microsoft**: **Sim** (padrão) permite usar uma lista de compatibilidade da Microsoft. **Não** impede a lista de compatibilidade da Microsoft no Microsoft Edge. Esta lista da Microsoft ajuda o Microsoft Edge a exibir corretamente sites com problemas de compatibilidade conhecidos.
- **Páginas de início de pré-carregamento e nova página de guia**: **Sim** (padrão) usa o comportamento padrão do sistema operacional, que pode ser pré-carregar essas páginas. O pré-carregamento minimiza o tempo para iniciar o Microsoft Edge e carrega novas guias. **Não** impede que o Microsoft Edge carregue páginas iniciais e a nova página da guia.
- **Páginas inicial de pré-inicialização e nova guia**: **Sim** (padrão) usa o comportamento padrão do sistema operacional, que pode ser inicializar essas páginas. Iniciar previamente ajuda o desempenho do Microsoft Edge e minimiza o tempo necessário para iniciar o Microsoft Edge. **Não** impede o Microsoft Edge de inicializar previamente as páginas inicial e a nova guia.

Selecione **OK** para guardar as alterações.

### <a name="favorites-and-search"></a>Favoritos e pesquisa

- **Mostrar barra de favoritos**: Escolha o que acontece com a barra de favoritos em qualquer página do Microsoft Edge. As opções são:
  - **Nas páginas inicial e nova guia**: Mostra a barra de favoritos quando o Microsoft Edge é iniciado e em todas as páginas da guia. Os usuários finais podem alterar essa configuração.
  - **Em todas as páginas**: Mostra a barra de favoritos em todas as páginas. Os usuários finais não podem alterar essa configuração.
  - **Oculto**: Oculta a barra de favoritos em todas as páginas. Os usuários finais não podem alterar essa configuração.
- **Permitir alterações em favoritos**: **Sim** (padrão) usa o padrão do sistema operacional, que permite aos usuários alterar a lista. **Não** impede que os usuários finais adicionem, importem, classifiquem ou editem a lista de favoritos.
  - **Lista de favoritos**: Adicione uma lista de URLs ao arquivo de favoritos. Por exemplo, adicione `http://contoso.com/favorites.html`.
- **Sincronizar favoritos entre** os navegadores da Microsoft (Somente desktop): **Sim** força o Windows a sincronizar os favoritos entre o Internet Explorer e o Microsoft Edge. Adições, exclusões, modificações e alterações de pedidos a favoritos são compartilhadas entre navegadores.  **Não** (padrão) usa o padrão do sistema operacional, que pode fornecer aos usuários a opção de sincronizar os favoritos entre os navegadores.
- **Mecanismo de pesquisa padrão**: Escolha o mecanismo de pesquisa padrão no dispositivo. Os utilizadores finais podem alterar este valor em qualquer altura. As opções são:
  - Mecanismo de pesquisa nas configurações do Microsoft Edge do cliente
  - Bing
  - Google
  - Instant
  - Valor personalizado: Na **URL XML de OpenSearch**, insira uma URL HTTPS com o arquivo XML que inclui o nome curto e a URL para o mecanismo de pesquisa, no mínimo. Por exemplo, introduza `https://www.contoso.com/opensearch.xml`.
- **Mostrar sugestões de pesquisa**: **Sim** (padrão) permite que o mecanismo de pesquisa sugira sites à medida que você digita frases de pesquisa na barra de endereços. **Não** impede esse recurso.
- **Permitir alterações no mecanismo de pesquisa**: **Sim** (padrão) permite que os usuários adicionem novos mecanismos de pesquisa ou alterem o mecanismo de pesquisa padrão no Microsoft Edge. Escolha **não** para impedir que os usuários personalizem o mecanismo de pesquisa.

  Essa configuração só está disponível quando executada no [modo normal (quiosque de vários aplicativos)](#use-microsoft-edge-kiosk-mode).

Selecione **OK** para guardar as alterações.

### <a name="privacy-and-security"></a>Privacidade e segurança

- **Permitir navegação InPrivate**: **Sim** (padrão) permite a navegação InPrivate no Microsoft Edge. Depois de fechar todas as guias InPrivate, o Microsoft Edge exclui os dados de navegação do dispositivo. **Não** impede que os usuários finais Abram sessões de navegação InPrivate.
- **Salvar histórico de navegação**: **Sim** (padrão) permitir salvar o histórico de navegação no Microsoft Edge. **Não** impede que o histórico de navegação seja salvo.
- **Limpar dados de navegação ao sair** (somente desktop): **Sim** limpa o histórico e procura dados quando o usuário sai do Microsoft Edge. **Não** (padrão) usa o padrão do sistema operacional, que pode armazenar em cache os dados de navegação.
- **Sincronizar as configurações do navegador entre os dispositivos do usuário**: Escolha como você deseja sincronizar as configurações do navegador entre os dispositivos. As opções são:
  - **Permitir**: Permitir a sincronização de configurações do navegador Microsoft Edge entre os dispositivos do usuário
  - **Bloquear e habilitar substituição de usuário**: Bloquear a sincronização das configurações do navegador Microsoft Edge entre os dispositivos do usuário. Os usuários podem substituir essa configuração.
  - **Bloquear**: Bloquear a sincronização da configuração do navegador Microsoft Edge entre os dispositivos dos usuários. Os usuários não podem substituir essa configuração.

Quando "bloquear e habilitar substituição de usuário" está selecionado, o usuário pode substituir a designação de administrador.

- **Permitir Gerenciador de senhas**: **Sim** (padrão) permite que o Microsoft Edge use automaticamente o Gerenciador de senhas, que permite que os usuários salvem e gerenciem senhas no dispositivo. **Não** impede que o Microsoft Edge use o Gerenciador de senhas.
- **Cookies**: Escolha como os cookies são manipulados no navegador da Web. As opções são:
  - **Permitir**: Os cookies são armazenados no dispositivo.
  - **Bloquear todos os cookies**: Os cookies não são armazenados no dispositivo.
  - **Bloquear somente cookies**de terceiros: Os cookies de terceiros ou parceiros não são armazenados no dispositivo.
- **Permitir preenchimento automático em formulários**: **Sim** (padrão) permite que os usuários alterem as configurações de preenchimento automático no navegador e populem campos de formulário automaticamente. **Não** desabilita o recurso de preenchimento automático no Microsoft Edge.
- **Enviar cabeçalhos do not Track**: **Sim** envia cabeçalhos do not Track para sites solicitando informações de acompanhamento (recomendado). **Não** (padrão) não envia cabeçalhos, o que permite que os sites acompanhem o usuário. O usuário pode configurar.
- **Mostrar endereço IP do localhost WebRTC**: **Sim** (padrão) permite que o endereço IP do localhost dos usuários seja mostrado ao fazer chamadas telefônicas usando esse protocolo. **Não** impede que o endereço IP do localhost dos usuários seja mostrado. 
- **Permitir coleta de dados de bloco dinâmico**: **Sim** (padrão) permite que o Microsoft Edge colete informações de blocos dinâmicos fixados no menu iniciar. **Não** impede a coleta dessas informações, o que pode fornecer aos usuários uma experiência limitada.
- O **usuário pode substituir erros de certificado**: **Sim** (padrão) permite que os usuários acessem sites que têm erros de protocolo SSL/TLS (segurança da camada de transporte). **Não** (recomendado para maior segurança) impede que os usuários acessem sites com erros SSL ou TLS.

Selecione **OK** para guardar as alterações.

### <a name="additional"></a>Adicionais

- **Permitir navegador Microsoft Edge** (somente dispositivos móveis): **Sim** (padrão) permite usar o navegador da Web Microsoft Edge no dispositivo móvel. **Não** impede o uso do Microsoft Edge no dispositivo. Se você escolher **não**, as outras configurações individuais se aplicarão somente ao desktop.
- **Permitir lista suspensa de barra de endereços**: **Sim** (padrão) permite que o Microsoft Edge mostre o menu suspenso da barra de endereços com uma lista de sugestões. **Não** impede o Microsoft Edge de mostrar uma lista de sugestões em uma lista suspensa quando você digita. Quando definido como **não**, você:
  - Ajude a minimizar a largura de banda de rede entre o Microsoft Edge e os serviços da Microsoft.
  - Desabilite a **exibição mostrar sugestões de pesquisa e site enquanto eu digitar** no Microsoft Edge > configurações.
- **Permitir modo de tela inteira**: **Sim** (padrão) permite que o Microsoft Edge use o modo de tela inteira, que mostra apenas o conteúdo da Web e oculta a interface do usuário do Microsoft Edge. **Não** impede o modo de tela inteira no Microsoft Edge.
- **Permitir a página de sinalizadores**: **Sim** (padrão) usa o padrão do sistema operacional, que pode permitir `about:flags` o acesso à página. A `about:flags` página permite que os usuários alterem as configurações do desenvolvedor e habilitem recursos experimentais. **Não** impede que os usuários finais acessem `about:flags` a página no Microsoft Edge.
- **Permitir ferramentas de desenvolvedor**: **Sim** (padrão) permite que os usuários usem as ferramentas de desenvolvedor F12 para criar e depurar páginas da Web por padrão. **Não** impede que os usuários finais usem as ferramentas de desenvolvedor F12.
- **Permitir JavaScript**: **Sim** (padrão) permite que scripts, como JavaScript, sejam executados no navegador Microsoft Edge. **Não** impede a execução de scripts java no navegador.
- O **usuário pode instalar extensões**: **Sim** (padrão) permite que os usuários finais instalem extensões do Microsoft Edge no dispositivo. **Não** impede a instalação.
- **Permitir Sideload de extensões de desenvolvedor**: **Sim** (padrão) usa o padrão do sistema operacional, que pode permitir o Sideload. O Sideload instala e executa extensões não verificadas. **Não** impede o Microsoft Edge de Sideload usando o recurso de **extensões de carregamento** . Ele não impede extensões de Sideload usando outras maneiras, como o PowerShell.
- **Extensões necessárias**: Escolha quais extensões não podem ser desativadas pelos usuários finais no Microsoft Edge. Insira os nomes da família de pacotes e selecione **Adicionar**. [Encontre um nome de família de pacotes (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) que fornece algumas diretrizes.

  Você também pode **importar** um arquivo CSV que inclui os nomes da família de pacotes. Ou então , exporte os nomes de família de pacotes que você inserir.

Selecione **OK** para guardar as alterações.

## <a name="network-proxy"></a>Proxy de rede

Essas configurações usam o [CSP da política do NetworkProxy](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), que também lista as edições do Windows com suporte.

- **Detectar automaticamente as configurações de proxy**: **Bloquear** desabilita o dispositivo de detectar automaticamente um script de configuração automática de proxy (PAC). **Não configurado** (padrão) habilita esse recurso. Quando habilitado, o dispositivo tenta localizar o caminho para um script PAC.
- **Usar script de proxy**: Escolha **permitir** para inserir um caminho para o script de PAC para configurar o servidor proxy. **Não configurado** (padrão) não permite que você insira a URL para um script de PAC.
  - **URL do endereço do script de instalação**: Insira a URL de um script de PAC que você deseja usar para configurar o servidor proxy.
- **Usar servidor proxy manual**: Escolha **permitir** para inserir manualmente o nome ou endereço IP e o número da porta TCP de um servidor proxy. **Não configurado** (padrão) não permite que você insira manualmente os detalhes de um servidor proxy.
  - **Endereço**: Insira o nome ou endereço IP do servidor proxy.
  - **Número da porta**: Insira o número da porta do seu servidor proxy.
  - **Exceções de proxy**: Insira as URLs que não devem usar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
  - **Ignorar servidor proxy para endereço local**: **Não configurado** (padrão) impede o uso de um servidor proxy para endereços locais na sua intranet. **Permitir** usa um servidor proxy para endereços locais.

Selecione **OK** para guardar as alterações.

## <a name="password"></a>Palavra-passe

Essas configurações usam o [CSP da política do DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), que também lista as edições do Windows com suporte.

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** (padrão) permite o acesso ao dispositivo sem uma senha. Aplica-se somente a contas locais. As senhas de conta de domínio permanecem configuradas pelo Active Directory (AD) e pelo Azure AD.

  - **Tipo obrigatório de palavra-passe**: Escolha o tipo de senha. As opções são:
    - **Não configurado**: A senha pode incluir números e letras.
    - **Numérica**: A senha deve ser apenas números.
    - **Alfanumérica**: A senha deve ser uma combinação de números e letras.
  - **Comprimento mínimo da palavra-passe**: Insira o número mínimo ou os caracteres necessários, de 4-16. Por exemplo, digite `6` para exigir pelo menos seis caracteres no comprimento da senha.
  
    > [!IMPORTANT]
    > Quando o requisito de senha for alterado em uma área de trabalho do Windows, os usuários serão afetados na próxima vez que entrarem, como é quando o dispositivo vai de ocioso para ativo. Os usuários com senhas que atendem ao requisito ainda são solicitados a alterar suas senhas.
    
  - **Número de falhas de início de sessão antes de apagar o dispositivo**: Insira o número de falhas de autenticação permitidas antes que o dispositivo possa ser apagado, até 11. O número válido que você inserir dependerá da edição. O [CSP DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) lista os valores com suporte. `0`(zero) pode desabilitar a funcionalidade de apagamento do dispositivo.

    Essa configuração também tem um impacto diferente dependendo da edição. Para obter detalhes específicos sobre essa configuração, consulte o [CSP DeviceLock/MaxDevicePasswordFailedAttempts](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Máximo de minutos de inatividade até o ecrã ser bloqueado**: Insira o período de tempo que um dispositivo deve ficar ocioso antes que a tela seja bloqueada.
  - **Expiração da palavra-passe (dias)** : Insira o período de tempo em dias em que a senha do dispositivo deve ser alterada, de 1-365. Por exemplo, digite `90` para expirar a senha após 90 dias.
  - **Impedir a reutilização de palavras-passe anteriores**: Insira o número de senhas usadas anteriormente que não podem ser usadas, de 1-24. Por exemplo, insira `5` para que os usuários não possam definir uma nova senha para sua senha atual ou com qualquer uma de suas quatro senhas anteriores.
  - **Exigir senha quando o dispositivo retornar do estado ocioso** (Mobile e Holographic): Escolha **exigir** para que os usuários precisem inserir uma senha para desbloquear o dispositivo depois de ficar ocioso. **Não configurado** (padrão) não exige um PIN ou senha quando o dispositivo é retomado do estado ocioso.
  - **Palavras-passe simples**: Definido como **Bloquear** para que os usuários não possam criar senhas simples `1234` , `1111`como ou. Defina como **não configurado** (padrão) para permitir que os usuários criem `1111`senhas como `1234` ou. Esta definição também permite ou bloqueia a utilização de palavras-passe por imagem do Windows.
- **Criptografia automática durante AADJ**: **Bloquear** impede a criptografia automática do dispositivo BitLocker quando o dispositivo estiver preparado para o primeiro uso, quando o dispositivo for ingressado no Azure AD. **Não configurado** (padrão) usa o padrão do sistema operacional, que pode habilitar a criptografia. Mais sobre a [criptografia de dispositivo do BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Segurança/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Política de padrão FIPS (FIPS)** : **Permitir** usa a política de padrão FIPS (FIPS), que é um padrão do governo dos EUA para criptografia, hash e assinatura. **Não configurado** (padrão) usa o padrão do sistema operacional, que não usa o FIPS.

  [CSP de criptografia/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticação de dispositivo do Windows Hello**: **Permitir que** os usuários usem um dispositivo complementar do Windows Hello, como um telefone, uma faixa de ADEQÜAÇÃO ou um dispositivo IOT, para entrar em um computador com Windows 10. **Não configurado** (padrão) usa o padrão do sistema operacional, o que pode impedir que os dispositivos do Windows Hello Companion se autentiquem com o Windows.

  [Autenticação/CSP AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Entrada na Web**: Habilita o suporte de entrada do Windows para provedores federados não ADFS (Serviços de Federação do Active Directory (AD FS)), como Security Assertion Markup Language (SAML). O SAML usa tokens seguros que fornecem aos navegadores da Web uma experiência de logon único (SSO). As opções são:

  - **Não configurado** (predefinição): Usa o padrão do sistema operacional no dispositivo.
  - **Habilitado**: O provedor de credenciais da Web está habilitado para entrada.
  - **Desativado**: O provedor de credenciais da Web está desabilitado para entrar.

  [Autenticação/CSP EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Domínio de locatário do Azure ad preferencial**: Insira um nome de domínio existente na sua organização do Azure AD. Quando os usuários nesse domínio entram, eles não precisam digitar o nome de domínio. Por exemplo, introduza `contoso.com`. Os usuários no `contoso.com` domínio podem entrar usando seu nome de usuário, `abby`como, em vez de `abby@contoso.com`.

  [Autenticação/CSP PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Selecione **OK** para guardar as alterações.

## <a name="per-app-privacy-exceptions"></a>Exceções de privacidade por aplicação

Você pode adicionar aplicativos que devem ter um comportamento de privacidade diferente do que você define em "privacidade padrão".

- **Nome do pacote**: Nome da família de pacotes de aplicativos.
- **Nome do aplicativo**: O nome do aplicativo.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se este aplicativo pode acessar o nome de usuário, a imagem e outras informações de contato.
- **Aplicativos em segundo plano**: Defina se este aplicativo pode ser executado em segundo plano.
- **Calendário**: Defina se este aplicativo pode acessar o calendário.
- **Histórico de chamadas**: Defina se este aplicativo pode acessar meu histórico de chamadas.
- **Câmara**: Defina se este aplicativo pode acessar a câmera.
- **Contatos**: Defina se este aplicativo pode acessar contatos.
- **Email**: Defina se este aplicativo pode acessar e enviar emails.
- **Local**: Defina se este aplicativo pode acessar informações de local.
- **Mensagens**: Defina se este aplicativo pode ler ou enviar mensagens de texto ou MMS.
- **Microfone**: Defina se este aplicativo pode usar o microfone.
- **Movimento**: Defina se este aplicativo pode acessar informações de movimento do dispositivo.
- **Notificações**: Defina se este aplicativo pode acessar notificações.
- **Telefone**: Defina se este aplicativo pode acessar o telefone.
- **Rádios**: Alguns aplicativos usam rádios (por exemplo, Bluetooth) em seu dispositivo para enviar e receber dados e precisam ativar ou desativar essas rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se este aplicativo pode acessar suas tarefas.
- **Dispositivos confiáveis**: Escolha se este aplicativo pode usar dispositivos confiáveis. Os dispositivos confiáveis são o hardware que você já conectou ou o hardware que vem com o dispositivo. Por exemplo, use TVs, projetores e assim por diante, como dispositivos confiáveis.
- **Comentários e diagnósticos**: Defina se este aplicativo pode acessar informações de diagnóstico.
- **Sincronizar com dispositivos**: Escolha se este aplicativo pode compartilhar e sincronizar informações automaticamente com dispositivos sem fio que não emparelham explicitamente com o dispositivo.

Selecione **OK** para guardar as alterações.

## <a name="personalization"></a>Personalização

Essas configurações usam o [CSP de política de personalização](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), que também lista as edições do Windows com suporte.

- **URL da imagem de fundo da área de trabalho (somente desktop)** : Insira a URL para uma imagem no formato. jpg,. jpeg ou. png que você deseja usar como o papel de parede da área de trabalho do Windows. Os utilizadores não podem alterar a imagem. Por exemplo, introduza `https://contoso.com/logo.png`.

Selecione **OK** para guardar as alterações.

## <a name="printer"></a>Impressora

- **Impressoras**: Lista de impressoras locais que foram adicionadas.
- **Impressora padrão**: Defina a impressora padrão.
- **Acesso do usuário para adicionar novas impressoras**: Permitir ou bloquear o uso de impressoras locais.

Selecione **OK** para guardar as alterações.

## <a name="privacy"></a>Privacidade

Essas configurações usam o [CSP de política de privacidade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), que também lista as edições do Windows com suporte.

- **Personalização de entrada**: **Bloquear** impede o uso de voz para ditado e para se comunicar com a Cortana e outros aplicativos que usam o reconhecimento de fala baseado em nuvem da Microsoft. Ele está desabilitado e os usuários não podem habilitar o reconhecimento de fala online usando as configurações. **Não configurado** (padrão) permite que os usuários escolham. Se você permitir esses serviços, a Microsoft poderá coletar dados de voz para melhorar o serviço.
- **Aceitação automática dos prompts de consentimento do usuário de privacidade e emparelhamento**: Escolha **permitir** para que o Windows possa aceitar automaticamente as mensagens de consentimento de emparelhamento e privacidade ao executar aplicativos. **Não configurado** (padrão) impede a aceitação automática da janela de consentimento do usuário de privacidade e emparelhamento ao abrir aplicativos.
- **Publicar as atividades do utilizador**: **Bloquear** impede experiências compartilhadas e a descoberta de recursos usados recentemente no feed de atividades. **Não configurado** (padrão) habilita esse recurso para que os aplicativos possam publicar atividades do usuário final.
- **Apenas atividades locais**: **Bloquear** impede experiências compartilhadas e a descoberta de recursos usados recentemente no alternador de tarefas, com base apenas na atividade local. **Não configurado** (padrão) habilita esse recurso.

Você pode configurar informações que todos os aplicativos no dispositivo podem acessar. Além disso, defina exceções em uma base por aplicativo usando **exceções de privacidade por aplicativo**.

Selecione **OK** para guardar as alterações.

### <a name="exceptions"></a>Exceções

- **Informações da conta**: Defina se este aplicativo pode acessar o nome de usuário, a imagem e outras informações de contato.
- **Aplicativos em segundo plano**: Defina se este aplicativo pode ser executado em segundo plano.
- **Calendário**: Defina se este aplicativo pode acessar o calendário.
- **Histórico de chamadas**: Defina se este aplicativo pode acessar meu histórico de chamadas.
- **Câmara**: Defina se este aplicativo pode acessar a câmera.
- **Contatos**: Defina se este aplicativo pode acessar contatos.
- **Email**: Defina se este aplicativo pode acessar e enviar emails.
- **Local**: Defina se este aplicativo pode acessar informações de local.
- **Mensagens**: Defina se este aplicativo pode ler ou enviar mensagens de texto ou MMS.
- **Microfone**: Defina se este aplicativo pode usar o microfone.
- **Movimento**: Defina se este aplicativo pode acessar informações de movimento do dispositivo.
- **Notificações**: Defina se este aplicativo pode acessar notificações.
- **Telefone**: Defina se este aplicativo pode acessar o telefone.
- **Rádios**: Alguns aplicativos usam rádios (por exemplo, Bluetooth) em seu dispositivo para enviar e receber dados e precisam ativar ou desativar essas rádios. Defina se esta aplicação pode controlar estes rádios.
- **Tarefas**: Defina se este aplicativo pode acessar suas tarefas.
- **Dispositivos confiáveis**: Escolha se este aplicativo pode usar dispositivos confiáveis. Os dispositivos confiáveis são o hardware que você já conectou ou o hardware que acompanha o dispositivo. Por exemplo, use TVs, projetores e assim por diante, como dispositivos confiáveis.
- **Comentários e diagnósticos**: Escolha se este aplicativo pode acessar informações de diagnóstico.
- **Sincronização com dispositivos** – defina se esta aplicação pode partilhar e sincronizar automaticamente informações com dispositivos sem fios que não sejam emparelhados especificamente com o PC, tablet ou telefone.

Selecione **OK** para guardar as alterações.

## <a name="projection"></a>Projeção

Essas configurações usam o [CSP da política do WirelessDisplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), que também lista as edições do Windows com suporte.

- **Entrada do usuário de receptores de exibição sem fio**: **Bloquear** impede a entrada do usuário de receptores de vídeo sem fio. **Não configurado** (padrão) permite que uma exibição sem fio envie teclado, mouse, caneta e entrada por toque de volta para o dispositivo de origem.
- **Projeção neste computador**: **Bloquear** impede que outros dispositivos localizem o dispositivo para projeção. **Não configurado** (padrão) permite que o dispositivo seja detectável e possa projetar no dispositivo acima da tela de bloqueio.
- **Exigir PIN para emparelhamento**: Escolha **exigir** para sempre solicitar um PIN ao se conectar a um dispositivo de projeção. **Não configurado** (padrão) não requer um PIN para emparelhar o dispositivo a um dispositivo de projeção.

Selecione **OK** para guardar as alterações.

## <a name="reporting-and-telemetry"></a>Relatórios e telemetria

- **Partilhar dados de utilização**: Escolha o nível de dados de diagnóstico que é enviado. As opções são:
  - **Não configurado**: Nenhum dado é compartilhado.
  - **Segurança**: Informações necessárias para ajudar a manter o Windows mais seguro, incluindo dados sobre as configurações de componentes de telemetria e experiência do usuário conectado, a ferramenta de remoção de software mal-intencionado e o Windows Defender.
  - **Básico**: Informações básicas do dispositivo, incluindo dados relacionados à qualidade, compatibilidade de aplicativos, dados de uso do aplicativo e dados do nível de segurança.
  - **Aprimorado**: Informações adicionais, incluindo: como o Windows, o Windows Server, o System Center e os aplicativos são usados, como eles executam, dados de confiabilidade avançados e dados dos níveis básico e de segurança.
  - **Completo**: Todos os dados necessários para identificar e ajudar a corrigir problemas, além de dados dos níveis de segurança, básicos e aprimorados.

  [CSP do sistema/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Enviar dados de navegação do Microsoft Edge para Microsoft 365 Analytics**: Para usar esse recurso, defina as configurações de **dados de uso do compartilhamento** como **avançado** ou **completo**. Esse recurso controla quais dados o Microsoft Edge envia para Microsoft 365 análise para dispositivos empresariais com uma ID comercial configurada. As opções são:
  - **Não configurado**: Usa o padrão do sistema operacional, que pode não enviar nenhum dado de histórico de navegação
  - **Somente enviar dados da intranet**: Permite que o administrador envie o histórico de dados da intranet
  - **Somente enviar dados da Internet**: Permite que o administrador envie o histórico de dados da Internet
  - **Enviar dados da intranet e da Internet**: Permite que o administrador envie histórico de dados da intranet e da Internet

  [CSP do navegador/ConfigureTelemetryForMicrosoft365Analytics](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Servidor proxy**de telemetria: Insira o nome de domínio totalmente qualificado (FQDN) ou o endereço IP de um servidor proxy para encaminhar as experiências de usuário conectadas e as solicitações de telemetria usando uma conexão protocolo SSL (SSL). O formato para esta definição é *servidor*:*porta*. Se o proxy nomeado falhar ou se um proxy não for inserido ao habilitar essa política, os dados de experiência de usuário conectados e telemetria não serão enviados e permanecerão no dispositivo local.

  Formatos de exemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [CSP do sistema/TelemetryProxy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Selecione **OK** para guardar as alterações.

## <a name="search"></a>Pesquisa

Essas configurações usam o [CSP de política de pesquisa](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), que também lista as edições do Windows com suporte. 

- **Pesquisa segura (somente dispositivos móveis)** : Controle como a Cortana filtra conteúdo adulto nos resultados da pesquisa. As opções são:
  - **Definido pelo usuário**: Permitir que os usuários finais escolham suas próprias configurações.
  - **Estrito**: Filtragem mais alta contra conteúdo adulto.
  - **Moderado**: Filtragem moderada contra conteúdo adulto. Os resultados de pesquisa válidos não são filtrados.
- **Exibir resultados da Web na pesquisa**: Quando definido como **Bloquear**, os usuários não podem pesquisar e os resultados da Web não são mostrados na pesquisa. **Não configurado** (padrão) permite que os usuários pesquisem a Web e os resultados sejam mostrados no dispositivo.

Selecione **OK** para guardar as alterações.

## <a name="start"></a>Start

Essas configurações usam o [CSP de política inicial](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), que também lista as edições do Windows com suporte.  

- **Layout do menu iniciar**: Substitua o layout de início padrão e personalize o menu iniciar em dispositivos de desktop. Carregue um arquivo XML que inclui suas personalizações, incluindo a ordem em que os aplicativos são listados e muito mais. Os usuários não podem alterar o layout do menu iniciar inserido.
- **Fixe sites a blocos no menu iniciar**: Importe imagens do Microsoft Edge que são mostradas como links no menu Iniciar do Windows para dispositivos de desktop.
- **Desafixar aplicativos da barra de tarefas**: **Bloquear** impede que os usuários desafixam aplicativos da barra de tarefas. **Não configurado** (padrão) permite que os usuários desafixem aplicativos da barra de tarefas.
- **Troca rápida de usuário**: **Bloquear** impede a alternância entre os usuários que fizeram logon simultaneamente sem fazer logoff. **Não configurado** (padrão) mostra o **usuário** do comutador no bloco do usuário.
- **Aplicativos mais usados**: **Bloquear** oculta a exibição dos aplicativos mais usados no menu iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os aplicativos mais usados.
- **Aplicativos adicionados recentemente**: **Bloquear** oculta aplicativos adicionados recentemente da exibição no menu iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os aplicativos adicionados recentemente no menu iniciar.
- **Modo de tela inicial**: Escolha como a tela inicial é mostrada. As opções são:
  - **Definido pelo usuário**: Não força o tamanho do início. Os usuários podem definir o tamanho.
  - **Tela inteira**: Força um tamanho de tela inicial.
  - **Tela não completa**: Forçar o tamanho de não-tela inicial.
- **Itens abertos recentemente nas listas de atalhos**: **Bloquear** oculta a exibição de listas de atalhos recentes no menu iniciar e na barra de tarefas. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (padrão) mostra os itens abertos recentemente no atalhos.
- **Lista de aplicativos**: Escolha como as listas todos os aplicativos são mostradas. As opções são:
  - **Definido pelo usuário**: Nenhuma configuração é forçada. Os usuários escolhem como a lista de aplicativos é mostrada no dispositivo.
  - **Recolher**: Ocultar a lista de todos os aplicativos.
  - **Recolha e desabilite o aplicativo Configurações**: Oculte a lista todos os aplicativos e desabilite **Mostrar lista de aplicativos no menu iniciar** no aplicativo configurações.
  - **Remove e desabilita o aplicativo Configurações**: Ocultar a lista todos os aplicativos, remover todos os aplicativos e desabilitar **Mostrar lista de aplicativos no menu iniciar** no aplicativo configurações.
- **Botão de energia**: **Bloquear** oculta o botão de energia da exibição no menu iniciar. **Não configurado** (padrão) mostra o botão de energia.
- **Bloco do usuário**: **Bloquear** oculta o bloco do usuário de mostrar no menu iniciar. **Não configurado** (padrão) mostra o bloco do usuário e também define as seguintes configurações:
  - **Bloqueio**: **Bloquear** oculta a opção de **bloqueio** da exibição no bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra a opção de **bloqueio** .
  - **Sair**: **Bloquear** oculta a opção **sair** da exibição no bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra a opção **sair** .
- **Desligar**: **Bloquear** oculta as opções de **atualização e** desligamento e desligamento da exibição no botão de energia no menu iniciar. **Não configurado** (padrão) mostra essas opções.
- **Suspensão**: **Bloquear** oculta a opção de **suspensão** da exibição no botão de energia no menu iniciar. **Não configurado** (padrão) mostra essa opção.
- **Hibernação**: **Bloquear** oculta a opção **hibernar** da exibição no botão de energia no menu iniciar. **Não configurado** (padrão) mostra essa opção.
- **Alternar conta**: **Bloquear** oculta a **conta** do comutador de mostrar no bloco do usuário no menu iniciar. **Não configurado** (padrão) mostra essa opção.
- **Opções**de reinicialização:  **Bloquear** oculta as opções de **atualização e** reinicialização e reinicialização de mostrar no botão de energia no menu iniciar. **Não configurado** (padrão) mostra essas opções.
- **Documentos em Iniciar**: Oculte ou mostre a pasta documentos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Downloads no início**: Ocultar ou mostrar a pasta de downloads no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Explorador de arquivos no início**: Oculte ou mostre o explorador de arquivos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Grupo doméstico no início**: Ocultar ou mostrar o atalho do grupo doméstico no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Música em Iniciar**: Oculte ou mostre a pasta música no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Rede em Iniciar**: Ocultar ou mostrar Entrada na Rede menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Pasta pessoal no início**: Ocultar ou mostrar a pasta pessoal no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Imagens no início**: Oculte ou mostre a pasta para imagens no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Configurações em Iniciar**: Oculte ou exiba o atalho configurações no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.
- **Vídeos no início**: Oculte ou mostre a pasta para vídeos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma configuração é forçada. Os usuários optam por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculto e desabilita a configuração no aplicativo configurações.
  - **Mostrar**: O atalho é mostrado e desabilita a configuração no aplicativo configurações.

Selecione **OK** para guardar as alterações.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para Microsoft Edge**: **Exigir** desativa o Windows Defender SmartScreen e impede que os usuários o liguem. **Não configurado** (padrão) ativa o SmartScreen. Ajuda a proteger os usuários contra possíveis ameaças e impede que os usuários o desativem.

  O Microsoft Edge usa o Windows Defender SmartScreen (ativado) para proteger os usuários contra possíveis golpes de phishing e software mal-intencionado.

  [CSP do navegador/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Acesso ao site mal-intencionado**: O **bloco** impede que os usuários ignorem os avisos do Filtro SmartScreen do Windows Defender e os bloqueia de ir para o site. **Não configurado** (padrão) permite que os usuários ignorem os avisos e continuem no site.

  [CSP do navegador/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Download de arquivo não verificado**: O **bloco** impede que os usuários ignorem os avisos do Filtro SmartScreen do Windows Defender e os bloqueiam de baixar arquivos não verificados. **Não configurado** (padrão) permite que os usuários ignorem os avisos e continuem a baixar os arquivos não verificados.

  [CSP do navegador/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

Selecione **OK** para guardar as alterações.

## <a name="windows-spotlight"></a>Destaque do Windows

Essas configurações usam o [CSP da política de experiência](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), que também lista as edições do Windows com suporte.

- **Destaque do Windows**: **Bloquear** desativa o destaque do Windows na tela de bloqueio, dicas do Windows, recursos de consumidor da Microsoft e outros recursos relacionados. Se seu objetivo é minimizar o tráfego de rede dos dispositivos, defina-o como **Bloquear**. **Não configurado** (padrão) permite recursos de destaque do Windows e pode ser controlado por usuários finais. Quando habilitado, você também pode permitir ou bloquear as seguintes configurações:

  - **Destaque do Windows na tela de bloqueio**: **Bloquear** impede que o destaque do Windows exiba informações na tela de bloqueio do dispositivo. **Não configurado** (padrão) habilita esse recurso.
  - **Sugestões de terceiros no destaque do Windows**: **Bloquear** impede o destaque do Windows de sugerir conteúdo que não está publicado pela Microsoft. **Não configurado** (padrão) permite sugestões de conteúdo e de aplicativo de editores de software de parceiros em recursos de destaque do Windows, como o destaque da tela de bloqueio, aplicativos sugeridos no menu iniciar e dicas do Windows.
  - **Recursos do consumidor**: **Blocos** desligam experiências que normalmente são apenas para consumidores, como sugestões de início, notificações de associação, instalação de aplicativo de experiência de lançamento e blocos de redirecionamento. **Não configurado** (predefinição) permite estas funcionalidades.
  - **Dicas do Windows**: **Bloquear** desabilita as dicas pop-up do Windows. **Não configurado** (padrão) permite que as dicas do Windows sejam exibidas.
  - **Destaque do Windows na central de ações**: **Bloquear** impede que notificações de destaque do Windows sejam exibidas na central de ações. **Não configurado** (padrão) pode mostrar notificações na central de ações que sugerem aplicativos ou recursos para ajudar os usuários a serem mais produtivos no Windows.
  - **Personalização do destaque do Windows**: **Bloquear** impede que o Windows use dados de diagnóstico para fornecer experiências personalizadas ao usuário. **Não configurado** (padrão) permite que a Microsoft use dados de diagnóstico para fornecer recomendações, dicas e ofertas personalizadas para personalizar o Windows para as necessidades do usuário.
  - **Experiência do Windows Welcome**: **Bloquear** desativa o recurso de experiência do Windows Welcome do Windows em destaque. A experiência de boas-vindas do Windows não mostrará quando houver atualizações e alterações no Windows e em seus aplicativos. **Não configurado** (padrão) permite que a experiência de boas-vindas do Windows mostre as informações do usuário sobre os recursos novos ou atualizados.

Selecione **OK** para guardar as alterações.

## <a name="windows-defender-antivirus"></a>Antivírus do Windows Defender

Essas configurações usam o [CSP de política do defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), que também lista as edições do Windows com suporte.

- **Monitoramento em tempo real**: **Habilitar** impede a verificação em tempo real de malware, spyware e outros softwares indesejados. **Não configurado** (padrão) permite esse recurso.
- **Monitoramento de comportamento**: **Habilitar** impede que o defender Verifique certos padrões conhecidos de atividade suspeita em dispositivos. **Não configurado** (padrão) permite o monitoramento de comportamento do Windows Defender.
- **Sistema de inspeção de rede (NIS)** : O NIS ajuda a proteger dispositivos contra explorações baseadas em rede. Utiliza as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e bloquear tráfego malicioso.
- **Verificar todos os downloads**: Controla se o Defender analisa todos os ficheiros transferidos da Internet.
- **Verificar scripts carregados nos navegadores da Web da Microsoft**: **Não configurado** (padrão) permite que o defender Verifique os scripts que são usados no Internet Explorer. **Habilitar** impede esta verificação.
- **Acesso do usuário final ao defender**: **Bloquear** oculta a interface do usuário do Windows Defender de usuários finais. Todas as notificações do Windows Defender também são suprimidas. **Não configurado** (padrão) permite que o usuário acesse a interface de usuário do Windows Defender. Quando esta definição for alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.
- **Intervalo de atualização de assinatura (em horas)** : Insira o intervalo para o qual o defender verifica novos arquivos de assinatura, de 0-24. As opções são:

  - **Não configurado** os
  - Não **verificar**: O defender não verifica novos arquivos de assinatura.
  - **1-24**: `1` verifica a cada hora `2` , verifica a cada duas `24` horas, verifica todos os dias e assim por diante.
- **Monitorar atividade de arquivos e programas**: Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos.
- **Dias antes da exclusão de malware em quarentena**: Continue acompanhando o malware resolvido durante o número de dias que você insere para que você possa verificar manualmente os dispositivos afetados anteriormente. Se você definir o número de dias como **0**, o malware permanecerá na pasta de quarentena e não será removido automaticamente. Quando definido como `90`, os itens de quarentena são armazenados por 90 dias no sistema e, em seguida, removidos.
- **Limite de uso da CPU durante uma verificação**: Limite a quantidade de CPU que as verificações têm permissão para usar, de **1** a **100**.
- **Verificar arquivos mortos**: **Habilitar** impede que o defender examine arquivos mortos, como arquivos zip ou cab. **Não configurado** (padrão) permite essa verificação.
- **Examinar mensagens de email recebidas**: **Habilitar** permite que o defender Verifique mensagens de email à medida que elas chegam no dispositivo. **Não configurado** (padrão) impede a verificação de email.
- **Verificar unidades removíveis durante uma verificação completa**: **Habilitar** impede verificações completas de unidades removíveis. **Não configurado** (padrão) permite que o defender Verifique unidades removíveis, como cartões USB.
- **Verificar unidades de rede mapeadas durante uma verificação completa**: **Habilitar** permite que o defender examine arquivos em unidades de rede mapeadas. **Não configurado** (padrão) impede a verificação completa. Se os arquivos na unidade forem somente leitura, o defender não poderá remover nenhum malware encontrado neles.
- **Verificar arquivos abertos de pastas de rede**: **Não configurado** (padrão) permite que o defender Verifique arquivos em unidades de rede compartilhadas, como arquivos acessados de um caminho UNC. **Habilitar** impede esta verificação. Se os arquivos na unidade forem somente leitura, o defender não poderá remover nenhum malware encontrado neles.
- **Proteção da nuvem**: **Não configurado** (padrão) permite que o Microsoft Active Protection Service receba informações sobre a atividade de malware de dispositivos que você gerencia. **Habilitar** bloqueia esse recurso.
- **Avisar os usuários antes do envio de exemplo**: Controla se arquivos potencialmente mal-intencionados que podem exigir análise adicional são enviados automaticamente à Microsoft. As opções são:
  - **Não configurado**
  - **Sempre avisar**
  - **Avisar antes de enviar dados pessoais**
  - **Nunca enviar dados**
  - **Enviar todos os dados sem avisar**: Os dados são enviados automaticamente

- **Tempo para executar uma verificação rápida diária**: Escolha a hora para executar uma verificação rápida diária. **Não configurado** não executa uma verificação diária. Se você quiser mais personalização, configure o **tipo de verificação do sistema para executar** a configuração.

  [CSP do defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Tipo de verificação do sistema a ser executada**: Agende uma verificação do sistema, incluindo o nível de verificação e o dia e hora para executar a verificação. As opções são:
  - **Não configurado**: Não agenda uma verificação do sistema no dispositivo. Os usuários finais podem executar verificações manualmente conforme necessário ou desejados em seus dispositivos.
  - **Desabilitar**: Desabilita qualquer verificação do sistema no dispositivo. Escolha esta opção se você estiver usando uma solução antivírus de parceiro que verifica os dispositivos.
  - **Análise rápida**: Examina os locais comuns em que pode haver malware registrado, como chaves do registro e pastas de inicialização conhecidas do Windows.
    - **Dia agendado**: Escolha o dia para executar a verificação.
    - **Hora agendada**: Escolha a hora para executar a verificação.
  - **Análise completa**: Examina os locais comuns em que pode haver malware registrado, além de examinar todos os arquivos e pastas no dispositivo.
    - **Dia agendado**: Escolha o dia para executar a verificação.
    - **Hora agendada**: Escolha a hora para executar a verificação.

  Essa configuração pode entrar em conflito com o **tempo para executar uma configuração de verificação rápida diária** . Algumas recomendações:

  - Para executar uma verificação rápida diária, configure o **tempo para executar uma configuração de verificação rápida diária** .
  - Para executar uma verificação rápida diária e uma verificação completa toda semana, configure o **tempo para executar uma verificação rápida diária**. Defina o **tipo de verificação do sistema a ser executada** em uma verificação completa com o dia e a hora.
  - Não configure o **tempo para executar uma configuração de verificação rápida diária** simultaneamente com o **tipo de verificação do sistema para executar** a **verificação rápida**. Essas configurações podem entrar em conflito e uma verificação pode não ser executada.
  - Para executar uma verificação rápida toda terça-feira às 18h, configure o **tipo de verificação do sistema para executar** a configuração.

  [CSP do defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP do defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP do defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Detectar aplicativos potencialmente**indesejados: Escolha o nível de proteção quando o Windows detectar aplicativos potencialmente indesejados. As opções são:
  - **Não configurado** (predefinição): A proteção de aplicativos potencialmente indesejados do Windows Defender está desabilitada.
  - **Bloquear**: O Windows Defender detecta aplicativos potencialmente indesejados e os itens detectados são bloqueados. Esses itens são mostrados em histórico junto com outras ameaças.
  - **Auditoria**: O Windows Defender detecta aplicativos potencialmente indesejados, mas não realiza nenhuma ação. Você pode examinar as informações sobre os aplicativos que o Windows Defender tomaria em ação. Por exemplo, pesquise eventos criados pelo Windows Defender no Visualizador de Eventos.

  Para obter mais informações sobre aplicativos potencialmente indesejados, consulte [detectar e bloquear aplicativos potencialmente](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)indesejados.

- **Ações sobre ameaças de malware detectadas**: Escolha as ações que você deseja que o defender assuma para cada nível de ameaça que detecta: baixa, moderada, alta e grave. Se não for possível, o Windows Defender escolherá a melhor opção para garantir que a ameaça seja corrigida. As opções são:
  - **Limpar**
  - **Quarentena**
  - **Remove**
  - **Permitir**
  - **Definido pelo utilizador**
  - **Bloquear**

Selecione **OK** para guardar as alterações.

### <a name="windows-defender-antivirus-exclusions"></a>Exclusões do Antivírus do Windows Defender

- **Arquivos e pastas a serem excluídos das verificações e da proteção em tempo real**: Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
- **Extensões de arquivo a serem excluídas das verificações e da proteção em tempo real**: Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Todos os arquivos com essas extensões não são incluídos em verificações em tempo real ou programadas.
- **Processos a serem excluídos das verificações e da proteção em tempo real**: Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Esses processos não estão incluídos em verificações em tempo real ou programadas.

Selecione **OK** para guardar as alterações.

## <a name="next-steps"></a>Passos seguintes

Para obter os detalhes técnicos adicionais de cada definição e quais as edições do Windows suportadas, veja [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referência de CSP de Políticas do Windows 10)
