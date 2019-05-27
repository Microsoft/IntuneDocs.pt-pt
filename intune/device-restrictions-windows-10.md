---
title: Definições de restrição de dispositivos para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Ver uma lista de todas as definições e suas descrições para a criação de restrições de dispositivos no Windows 10 e dispositivos posteriores. Utilize estas definições no perfil de configuração para controlar as capturas de ecrã, requisitos de palavra-passe, definições de local público, aplicações na loja, browser Microsoft Edge, defender do Windows, acesso para a cloud, o menu Iniciar e mais no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18f8e072037d0ca9065201e0d0db2a9a2f6074ce
ms.sourcegitcommit: 0f771585d3556c0af14500428d5c4c13c89b9b05
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174190"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Definições de dispositivos de 10 (e versões posteriores) do Windows para permitir ou restringir funcionalidades com o Intune

Este artigo apresenta e descreve todas as configurações diferentes, que pode controlar no Windows 10 e dispositivos mais recentes. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, definir regras de palavra-passe, personalizar o ecrã de bloqueio, utilize o Windows Defender e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos seus dispositivos Windows 10.

> [!Note]
> Nem todas as opções estão disponíveis em todas as edições do Windows. Para ver as edições suportadas, veja a [política de CSPs](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (abre-se outro web site da Microsoft).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>App Store

Utilizam estas definições a [ApplicationManagement política CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), que também apresenta uma lista de edições suportadas do Windows.

- **Loja de aplicações** (apenas móvel): **Não configurado** (predefinição) permite aos utilizadores finais acesso à loja de aplicações em dispositivos móveis. **Bloco** impede a utilização da loja de aplicações.
- **Atualização automática de aplicações da loja**: **Não configurado** (predefinição) permite que aplicações instaladas a partir da Microsoft Store sejam atualizadas automaticamente. **Bloco** impede que as atualizações de instalação automática.
- **Instalação de aplicação fidedigna**: Escolha se não Microsoft Store aplicações podem ser instaladas, também conhecido como sideloading. Sideloading é instalar e, em seguida, em execução ou testando um aplicativo que não está certificado pela Microsoft Store. Por exemplo, uma aplicação que é interna da sua empresa apenas. As opções são:
  - **Não configurado** (predefinição): Utiliza a predefinição do sistema operacional.
  - **Bloco**: Impede que o sideload. Não não possível instalar aplicações de não-Microsoft Store.
  - **Permitir**: Permite que o sideload. Aplicações de Microsoft Store não podem ser instaladas.
- **Desbloqueio de programador**: Permitir que as definições de programador do Windows, como permitir que as aplicações de sideload sejam modificadas pelos usuários finais. As opções são:
  - **Não configurado** (predefinição): Utiliza a predefinição do sistema operacional.
  - **Bloco**: Impede que as aplicações de modo e o sideload de programador.
  - **Permitir**: Permite que desenvolvedores modo e o sideload de aplicações.

  [Ativar o seu dispositivo para o desenvolvimento](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) tem mais informações sobre esta funcionalidade.

- **Dados de aplicação do utilizador partilhados**: Escolher **permitir** para partilhar dados de aplicação entre os diferentes utilizadores no mesmo dispositivo e com outras instâncias dessa aplicação. **Não configurado** (predefinição) impede a partilha dados com outros utilizadores e outras instâncias da mesma aplicação.
- **Utilizar apenas loja privada**: **Permitir** apenas permite que as aplicações sejam transferidas a partir de uma loja privada e não transferidas a partir da loja pública, incluindo um catálogo de varejo. **Não configurado** (predefinição) permite que as aplicações a serem baixados de uma privada, arquivo e um arquivo público.
- **Lançamento de aplicação originado pela Store**: **Bloco** desativa todas as aplicações que foram previamente instaladas no dispositivo ou transferidas a partir da Microsoft Store. **Não configurado** (predefinição) permite que estas aplicações abrir.
- **Instalar dados da aplicação no volume do sistema**: **Bloco** impede que as aplicações armazenem dados no volume do sistema do dispositivo. **Não configurado** (predefinição) permite que as aplicações armazenar dados no volume de disco do sistema.
- **Instalar aplicações na unidade do sistema**: **Bloco** impede que aplicações instalação na unidade do sistema no dispositivo. **Não configurado** (predefinição) permite que as aplicações instalar na unidade do sistema.
- **Gravador de jogo** (apenas ambiente de trabalho): **Bloco** desativa o jogo do Windows gravação e a difusão. **Não configurado** (predefinição) permite que a gravação e a difusão de jogos.
- **As aplicações da loja apenas**: **Exigir** força os utilizadores finais para instalarem apenas aplicações da Store de aplicação do Windows. **Não configurado** permite aos utilizadores finais instalar aplicações a partir de outros locais que não o Store de aplicação do Windows.

Selecione **OK** para guardar as alterações.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

Utilizam estas definições a [política de conectividade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) e [política de Wi-Fi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSPs, que também listam as edições suportadas do Windows.

- [Política de Wi-Fi CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Canal de dados via rede móvel**: Escolha se os utilizadores finais podem utilizar dados, como navegação na web, quando estiver ligado a uma rede celular. As opções são:
  - **Não configurado** (predefinição): Utiliza o padrão de sistema operacional, que pode permitir que o canal de dados via rede móvel. Os utilizadores finais podem desativá-la.
  - **Bloco**: Não permitir que o canal de dados via rede móvel. Os utilizadores finais não é possível ativá-la.
  - **Permitir (não editável)** : Permite que o canal de dados via rede móvel. Os utilizadores finais não pode desativá-la.

- **Roaming de dados**: **Bloco** impede que os dados via rede móveis em roaming no dispositivo. **Não configurado** (predefinição) permite o roaming entre redes ao aceder a dados.
- **VPN na rede celular**: **Bloco** impede o dispositivo de aceder a ligações VPN quando ligado a uma rede celular. **Não configurado** (predefinição) permite que a VPN utilizar qualquer ligação, incluindo rede móvel.
- **Roaming na rede celular de VPN**: **Bloco** para o dispositivo de aceder a ligações VPN quando está em roaming numa rede celular. **Não configurado** (predefinição) permite que as ligações VPN quando está em roaming.
- **Serviço de dispositivos ligados**: **Bloco** desativa o componente de plataforma de dispositivos ligados (CDP). CDP ativa a identificação e ligação a outros dispositivos (através de Bluetooth/LAN ou na cloud) para oferecer suporte a abrir uma aplicação remota, o sistema de mensagens remoto, sessões de aplicação remota e outras experiências entre dispositivos. **Não configurado** (predefinição) permite que o serviço de dispositivos ligados, o que permite a deteção e ligação a outros dispositivos Bluetooth.
- **NFC**: **Bloco** impede perto de recursos de comunicações (NFC) do campo. **Não configurado** (predefinição) permite aos utilizadores ativar e configurar funcionalidades de NFC no dispositivo.
- **Wi-Fi**: **Bloco** impede que os utilizadores e ativar, configurar e utilizar ligações Wi-Fi no dispositivo. **Não configurado** (predefinição) permite ligações Wi-Fi.
- **Ligar automaticamente a hotspots Wi-Fi**: **Bloco** impede que os dispositivos a ligar automaticamente a hotspots Wi-Fi. **Não configurado** (predefinição) permite que dispositivos ligar automaticamente a hotspots de Wi-Fi gratuitos e aceitar automaticamente quaisquer termos e condições para a ligação.
- **Configuração de Wi-Fi manual**: **Bloco** impede que dispositivos se liguem ao Wi-Fi fora de redes de instalação de servidor MDM. **Não configurado** (predefinição) permite que os utilizadores finais adicionar e configurar a sua própria rede de ligações Wi-Fi SSIDs.
- **Intervalo de deteção do Wi-Fi**: Introduza a frequência com que dispositivos verificar a existência de redes Wi-Fi. Introduza um valor entre 1 (mais frequente) para 500 (menos frequente). A predefinição é `0` (zero).

### <a name="bluetooth"></a>Bluetooth

Utilizam estas definições a [CSP de política de Bluetooth](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth); que também apresenta uma lista de edições suportadas do Windows.

- **Bluetooth**: **Bloco** impede os utilizadores de ativar o Bluetooth. **Não configurado** (predefinição) permite que o Bluetooth no dispositivo.
- **Deteção de Bluetooth**: **Bloco** impede o dispositivo de que está a ser detetável por outros dispositivos com Bluetooth ativado. **Não configurado** (predefinição) permite que outros dispositivos com Bluetooth ativado, como um headset, para detetar o dispositivo.
- **Pré-emparelhamento de Bluetooth**: **Bloco** impede que os dispositivos Bluetooth específicos para sejam emparelhados automaticamente com um dispositivo anfitrião. **Não configurado** (predefinição) permite o emparelhamento com o dispositivo host automática.
- **Publicidade do Bluetooth**: **Bloco** impede o dispositivo de envio de anúncios de Bluetooth. **Não configurado** (predefinição) permite que o dispositivo enviar os anúncios de Bluetooth.
- **Serviços Bluetooth permitidos**: **Adicione** uma lista de permitidos perfis e serviços Bluetooth como cadeias de caracteres hexadecimais, como `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [Guia de utilização de ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) tem mais informações sobre a lista de serviço.

Selecione **OK** para guardar as alterações.

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

Utilizam estas definições a [CSP de política de contas](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts); que também apresenta uma lista de edições suportadas do Windows.

- **Conta Microsoft**: **Bloco** impede que os utilizadores finais associar uma conta Microsoft com o dispositivo. **Não configurado** (predefinição) permite adicionar e utilizar uma conta Microsoft.
- **Conta não Microsoft**: **Bloco** impede os utilizadores de adicionar contas de terceiros usando a interface do usuário. **Não configurado** (predefinição) permite aos utilizadores adicionar contas de e-mail que não estão associadas a uma conta Microsoft.
- **Sincronização de definições para a conta Microsoft**: **Não configurado** (predefinição) permite que as definições de dispositivos e aplicações associadas uma conta Microsoft sejam sincronizadas entre dispositivos. **Bloco** impede que esta sincronização.
- **Assistente de início de sessão Microsoft Account**: Quando definido como **não configurado** (predefinição), os utilizadores finais podem iniciar e parar o **conta de início de sessão no Assistente do Microsoft** service (wlidsvc). Este serviço de sistema operacional permite que os utilizadores iniciem sessão respetiva conta Microsoft. **Desativar** impede que os utilizadores finais controla o serviço de Assistente de início de sessão no Microsoft (wlidsvc).

Selecione **OK** para guardar as alterações.

## <a name="cloud-printer"></a>Impressora em Cloud

Utilizam estas definições a [EnterpriseCloudPrint política CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint); que também apresenta uma lista de edições suportadas do Windows.

- **URL de deteção de impressora**: Introduza o URL para localizar impressoras em cloud. Por exemplo, introduza `https://cloudprinterdiscovery.contoso.com`.
- **URL de autoridade de acesso de impressora**: Introduza o URL de ponto final de autenticação para obter os tokens de OAuth. Por exemplo, introduza `https://azuretenant.contoso.com/adfs`.
- **GUID da aplicação de cliente nativo do Azure**: Introduza o GUID de um aplicativo de cliente é permitido obter OAuth tokens a partir de OAuthAuthority. Por exemplo, introduza `E1CF1107-FF90-4228-93BF-26052DD2C714`.
- **URI do recurso de serviço de impressão**: Introduza o URI do recurso OAuth para o serviço de impressão configurado no portal do Azure. Por exemplo, introduza `http://MicrosoftEnterpriseCloudPrint/CloudPrint`.
- **Impressoras máximas a consultar**: Introduza o número máximo de impressoras que deseja ser consultado. O valor predefinido é `20`.
- **O recurso de serviço de deteção de impressão URI**: Introduza o URI do recurso OAuth para a deteção de impressora serviço configurado no portal do Azure. Por exemplo, introduza `http://MopriaDiscoveryService/CloudPrint`.

> [!TIP]
> Depois de configurar uma [impressão de Cloud híbrida do Windows Server](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview), pode configurar estas definições e, em seguida, implementar nos seus dispositivos do Windows.

Selecione **OK** para guardar as alterações.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Aplicação de definições**: **Bloco** impede que os utilizadores finais a aceder à aplicação de definições do Windows. **Não configurado** (predefinição) permite aos utilizadores abrir a aplicação de definições no dispositivo.
  - **Sistema**: **Bloco** impede o acesso à área do sistema da aplicação de definições. **Não configurado** (predefinição) permite o acesso.
    - **Modificação das definições de energia e suspensão** (apenas ambiente de trabalho): **Bloco** impede os utilizadores alterem as definições de energia e suspensão no dispositivo. **Não configurado** (predefinição) permite aos utilizadores alterar energia e as definições de suspensão.
  - **dispositivos**: **Bloco** impede o acesso à área de dispositivos da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Rede de Internet**: **Bloco** impede o acesso à área de rede e Internet da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Personalização**: **Bloco** impede o acesso à área de personalização da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Aplicações**: **Bloco** impede o acesso à área de aplicações da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Contas**: **Bloco** impede o acesso à área de contas da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Hora e idioma**: **Bloco** impede o acesso à área de hora e idioma da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
    - **Modificação da hora do sistema**: **Bloco** impede os utilizadores alterem as definições de data e hora no dispositivo. **Não configurado** permite que os usuários alterar estas definições.
    - **Modificação das definições de região** (apenas ambiente de trabalho): **Bloco** impede os utilizadores alterem as definições de região no dispositivo. **Não configurado** permite que os usuários alterar estas definições.
    - **Modificação de definições de idioma (apenas ambiente de trabalho)** : **Bloco** impede os utilizadores alterem as definições de idioma no dispositivo. **Não configurado** permite que os usuários alterar estas definições.

      [Política de definições de CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Jogos**: **Bloco** impede o acesso à área de jogos da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Facilidade de acesso**: **Bloco** impede o acesso à área de Facilidade de acesso da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Privacidade**: **Bloco** impede o acesso à área de privacidade da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.
  - **Atualização e segurança**: **Bloco** impede o acesso à área de atualização e segurança da aplicação de definições no dispositivo. **Não configurado** (predefinição) permite o acesso.

Selecione **OK** para guardar as alterações.

## <a name="display"></a>Apresentar

Utilizam estas definições a [apresentar a política de CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display); que também apresenta uma lista de edições suportadas do Windows.

O dimensionamento PPP de GDI permite que as aplicações que não são compatível com DPI para ficar ciente por monitor DPI.

- **Ativar o dimensionamento de GDI para aplicações**: **Adicionar** as aplicações legadas que pretende que o dimensionamento PPP de GDI ativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento PPP de GDI é ativado para todos os aplicativos herdados na sua lista.

- **Desativar o dimensionamento da GDI para aplicações**: **Adicionar** as aplicações legadas que pretende que o dimensionamento PPP de GDI desativado. Por exemplo, introduza: `filename.exe` ou `%ProgramFiles%\Path\Filename.exe`.

  O dimensionamento PPP de GDI é desativado para todos os aplicativos herdados na sua lista.

Também pode **importação** um ficheiro. csv com a lista de aplicações.

Selecione **OK** para guardar as alterações.

## <a name="general"></a>Geral

Utilizam estas definições a [experiência de política de CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience); que também apresenta uma lista de edições suportadas do Windows. 

- **Captura de ecrã** (apenas móvel): **Bloco** impede que os utilizadores finais obter capturas de ecrã no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Copiar e colar (apenas móvel)** : **Bloco** impede que os utilizadores finais através de copiar e colar entre aplicações no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Anular inscrições manualmente**: **Bloco** impede que os utilizadores finais a eliminar a conta da área de trabalho utilizando o painel de controle da área de trabalho do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.

  Esta definição de política não se aplica se o computador estiver associado ao Azure AD e a inscrição automática está ativada.

- **Instalação do certificado de raiz manual** (apenas móvel): **Bloco** impede os utilizadores de instalar manualmente certificados de raiz e os certificados CAP intermédios. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Câmara**: **Bloco** impede que os utilizadores finais utilizando a câmara do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Sincronização de ficheiros do OneDrive**: **Bloco** impede que os utilizadores finais de sincronização de arquivos para o OneDrive do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Armazenamento amovível**: **Bloco** impede que os utilizadores finais através de dispositivos de armazenamento externo, como cartões SD com o dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Geolocalização**: **Bloco** impede os utilizadores de ativarem os serviços de localização no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Partilha da Internet**: **Bloco** impede que a ligação à Internet de partilha no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Reposição do telemóvel**: **Bloco** impede os utilizadores finais a eliminar os dados ou fazer uma reposição de fábrica no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Ligação USB**: **Bloco** impede o acesso a dispositivos de armazenamento externo através de uma ligação de USB no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade. Carregamento USB não é afetado por esta definição.
- **O modo Antirroubo** (apenas móvel): **Bloco** impede que os utilizadores finais selecionar a preferência de modo anti-roubo do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Cortana**: **Bloco** desativar o Assistente de voz Cortana no dispositivo. Quando o Cortana está desativada, os utilizadores ainda podem pesquisar para localizar itens no dispositivo. **Não configurado** (predefinição) permite que a Cortana.
- **Gravação de voz** (apenas móvel): **Bloco** impede que os utilizadores finais utilizando o gravador de voz do dispositivo no dispositivo. **Não configurado** (predefinição) permite que a gravação para as aplicações de voz.
- **Modificação do nome do dispositivo** (apenas móvel): **Bloco** impede que os utilizadores finais a alteração do nome do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Adicionar pacotes de aprovisionamento**: **Bloco** impede que o agente de configuração de tempo de execução que instala os pacotes de aprovisionamento do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Remover pacotes de aprovisionamento**: **Bloco** impede que o agente de configuração de tempo de execução que remove pacotes de aprovisionamento do dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Deteção de dispositivos**: **Bloco** impede o dispositivo de que está a ser detetados por outros dispositivos. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Comutador de tarefa** (apenas móvel): **Bloco** impede a troca de tarefas no dispositivo. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Diálogo de erro do cartão SIM** (apenas móvel): **Bloco** mensagens de erro de mostrar no dispositivo se nenhum cartão SIM for detetado. **Não configurado** (predefinição) mostra as mensagens de erro.
- **Área de trabalho de tinta**: Escolha se e como o utilizador aceder a área de trabalho do ink. As opções são:
  - **Não configurado** (predefinição): Se a área de trabalho do ink e o utilizador tem permissão para usá-lo acima do ecrã de bloqueio.
  - **Desativado no ecrã de bloqueio**: A área de trabalho do ink está ativada e a funcionalidade está ativada. No entanto, o utilizador não é possível aceder à mesma acima do ecrã de bloqueio.
  - **Desativado**: Acesso a tinta a área de trabalho está desativado. A funcionalidade está desativada.

  [Política de WindowsInkWorkspace CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Reimplementação automática**: Escolher **permitir** para que os utilizadores com direitos de administrador podem eliminar todos os dados de utilizador e as configurações usando **CTRL + Win + R** no ecrã de bloqueio do dispositivo. O dispositivo é automaticamente reconfigurado e reinscrito na gestão. **Não configurado** (predefinição) impede esta funcionalidade.
- **Exigir que os utilizadores liguem à rede durante a configuração de dispositivo**: Escolher **requerem** para que o dispositivo estabelece ligação a uma rede antes de ir após a página de rede durante a configuração do Windows. **Não configurado** (predefinição) permite aos utilizadores aceder após a página de rede, mesmo que não está ligado a uma rede.

  A definição entra em vigor na próxima vez que o dispositivo é apagado ou repor. Como qualquer outra configuração do Intune, o dispositivo tem de ser inscritos e gerido pelo Intune para receber as definições de configuração. Mas uma vez está inscrito e receber políticas, em seguida, repor o dispositivo impõe a definição durante a configuração seguinte do Windows.

- **Acesso de memória direto**: **Bloco** impede o acesso direto à memória (DMA) para todos os hot conectáveis PCI downstream portas até que um utilizador inicia sessão no Windows. **Ativado** (predefinição) permite o acesso a DMA, mesmo quando um utilizador não tem sessão iniciado.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Terminar a processos do Gerenciador de tarefas**: Esta definição determina se o não-administradores podem utilizar o Gestor de tarefas para tarefas de fim. **Bloco** impede que os usuários padrão (não-administradores) usando o Gerenciador de tarefas para terminar um processo ou tarefa no dispositivo. **Não configurado** (predefinição) permite que os usuários padrão encerrar um processo ou tarefa utilizando o Gestor de tarefas.

Selecione **OK** para guardar as alterações.

## <a name="locked-screen-experience"></a>Experiência de ecrã bloqueado

- **Notificações do Centro de ação (apenas móvel)** : **Bloco** impede que as notificações de centro de ação do Mostrar no ecrã de bloqueio do dispositivo. **Não configurado** (predefinição) permite aos utilizadores escolher as aplicações mostram notificações no ecrã de bloqueio.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **O URL da imagem de ecrã (apenas ambiente de trabalho) bloqueado**: Introduza o URL para uma imagem em formato JPG, JPEG ou PNG, que é utilizado como a imagem de fundo do ecrã de bloqueio do Windows. Por exemplo, introduza `https://contoso.com/image.png`. Esta definição bloqueia a imagem e não pode ser alterada posteriormente.
- **Tempo limite do ecrã configurável pelo utilizador (apenas móvel)** : **Permitir** permite que os utilizadores configurem o tempo limite do ecrã. **Não configurado** (predefinição) não dar aos utilizadores, esta opção.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **Cortana no ecrã bloqueado** (apenas ambiente de trabalho): **Bloco** impede que os utilizadores de interagir com a Cortana quando o dispositivo estiver no ecrã de bloqueio. **Não configurado** (predefinição) permite a interação com a Cortana.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Notificações de alerta no ecrã bloqueado**: **Bloco** impede que as notificações de alerta de mostrar no ecrã de bloqueio do dispositivo. **Não configurado** (predefinição) permite que estas notificações.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Tempo limite (apenas móvel) de ecrã**: Defina a duração (em segundos) a partir do ecrã de bloqueio para o ecrã se desliga. Valores suportados são de 11 a 1800. Por exemplo, introduza `300` para definir o tempo limite como 5 minutos.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

Selecione **OK** para guardar as alterações.

## <a name="messaging"></a>Sistema de mensagens

Utilizam estas definições a [CSP de política de mensagens](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging); que também apresenta uma lista de edições suportadas do Windows.

- **Sincronização (apenas móvel) de mensagens**: **Bloco** desativa as mensagens de texto seja uma cópia de segurança e restauro e para a sincronização de mensagens entre dispositivos do Windows. Desativar o ajuda a evitar o armazenamento de informações em servidores fora do controlo da organização. **Não configurado** (predefinição) permite aos utilizadores alterar estas definições e sincronizar suas mensagens.
- **MMS (apenas móvel)** : **Bloco** desativa MMS enviar e receber a funcionalidade do dispositivo. Para as empresas, utilize esta política para desativar os MMS nos dispositivos como parte do requisito de auditoria ou gestão. **Não configurado** (predefinição) permite MMS enviar e receber.
- **RCS (apenas móvel)** : **Bloco** desativa Rich Communication Services (RCS) enviar e receber a funcionalidade do dispositivo. Para as empresas, utilize esta política para desativar o RCS nos dispositivos como parte do requisito de auditoria ou gestão. **Não configurado** (predefinição) permite RCS enviar e receber.

Selecione **OK** para guardar as alterações.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

Utilizam estas definições a [CSP de política de browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), que também apresenta uma lista de edições suportadas do Windows.

### <a name="use-microsoft-edge-kiosk-mode"></a>Utilizar o modo de local público do Microsoft Edge

Alterar as definições disponíveis consoante aquilo que escolher. As opções são:

- **Não** (predefinição): Microsoft Edge não está em execução no modo de local público. Todas as definições do Microsoft Edge estão disponíveis para que possa alterar e configurar.
- **Digital/Interactive signage (quiosque de uma aplicação)** : Definições do Microsoft Edge filtros que são aplicáveis para o modo de local público do Microsoft Edge signage Digital/interativo para utilizam apenas em quiosques de aplicação única do Windows 10. Escolha esta definição para abrir uma tela de total de URL e mostrar apenas o conteúdo nesse Web site. [Configurar sinais digital](https://docs.microsoft.com/windows/configuration/setup-digital-signage) fornece mais informações sobre esta funcionalidade.
- **Navegação de público inPrivate (quiosque de uma aplicação)** : Utilizam as definições do Microsoft Edge de filtros que são aplicáveis para o modo InPrivate navegação Microsoft Edge quiosque público para quiosques de aplicação única do Windows 10. Executa uma versão de separador multi do Microsoft Edge.
- **Modo normal (quiosque de várias aplicações)** : Filtra as definições do Microsoft Edge que são aplicáveis ao modo de local público de borda do Microsoft Normal. Executa uma versão completa do Microsoft Edge com todas as funcionalidades de navegação.
- **Público, navegar (quiosque de várias aplicações)** : Filtra as definições do Microsoft Edge que são aplicáveis para a navegação pública num quiosque de várias aplicações do Windows 10.  Executa uma versão de separador multi do InPrivate do Microsoft Edge.

> [!TIP]
> Para obter mais informações sobre o que fazem essas opções, consulte [tipos de configuração de modo de local público de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Este perfil de restrições de dispositivo está diretamente relacionada com o perfil de local público que criar com o [definições de local público de Windows](kiosk-settings-windows.md). Para resumir:

1. Criar a [definições de local público de Windows](kiosk-settings-windows.md) perfil para executar o dispositivo no modo de local público. Selecione o Microsoft Edge que o aplicativo e defina o modo de local público do Microsoft Edge no perfil de local público.
2. Criar o perfil de restrições de dispositivo descrito neste artigo e configurar recursos específicos e as definições de permissão no Microsoft Edge. Certifique-se de que escolher o mesmo tipo de modo de local público de Microsoft Edge como selecionada no seu perfil de local público ([definições de local público de Windows](kiosk-settings-windows.md)). 

    [Definições do modo de local público de suportado](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) é um ótimo recurso.

> [!IMPORTANT] 
> Certifique-se de que atribuir este perfil do Microsoft Edge aos mesmos dispositivos como o seu perfil de local público ([definições de local público de Windows](kiosk-settings-windows.md)).

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Experiência de início

- **Iniciar o Microsoft Edge com**: Escolha quais páginas abrem quando o Microsoft Edge é iniciado. As opções são:
  - **Páginas iniciais de personalizado**: Introduza as páginas de início, tal como `http://www.contoso.com`. Microsoft Edge carrega as páginas de início que introduzir.
  - **Nova página de separador**: Tudo o que é introduzido de carga do Microsoft Edge a **novo separador URL** definição.
  - **Última página da sessão**: Microsoft Edge carrega a última página de sessão.
  - **Páginas iniciais nas definições da aplicação local**: Início do Microsoft Edge com a página inicial padrão definido pelo sistema operacional.

- **Permitir que o utilizador altere as páginas iniciais**: **Sim** (predefinição) permite que os utilizadores alterem as páginas de início. Os administradores podem usar o `EdgeHomepageUrls` para introduzir as páginas de início que os utilizadores veem por predefinição ao abrir o Microsoft Edge. **Não** bloqueia os utilizadores de alterar as páginas de início.
- **Permitir que o conteúdo da web na nova página da guia**: Quando definido como **Sim** (predefinição), o Microsoft Edge abre o URL introduzido na **novo separador URL** definição. Se o **novo separador URL** definição está em branco, o Microsoft Edge abre-se a nova página de separador listada nas definições do Microsoft Edge. Os utilizadores podem alterá-lo. Quando definido como **não**, Microsoft Edge é aberto um separador novo com uma página em branco. Os utilizadores não é possível alterá-lo.
- **Novo separador URL**: Introduza o URL para abrir a página novo separador. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.

- **Botão início**: Escolha o que acontece quando o botão de início está selecionado. As opções são:
  - **Páginas iniciais**: Abre-se a opção que selecionou no **iniciar o Microsoft Edge com** definição
  - **Nova página de separador**: Abre o URL que introduziu no **novo separador URL** definição.
  - **URL de botão de casa**: Introduza o URL para abrir. Por exemplo, introduza: `https://www.bing.com` ou `https://www.contoso.com`.
  - **Botão de ocultar Home**: Oculta o botão de início
- **Permitir que os utilizadores alterar o botão início**: **Sim** permite que os utilizadores alterem o botão de início. As alterações do utilizador substituem as definições de administrador para o botão de início. **Não** (predefinição) bloqueia os utilizadores de alterar a forma como o administrador configurou botão de início.
- **Mostrar página de tela de apresentação (apenas móvel)** : **Sim** (predefinição) mostra a primeira página de introdução de utilização no Microsoft Edge. **Não** pára a página de introdução de mostrar o primeiro tempo executa o Microsoft Edge. Esta funcionalidade permite às empresas, como as organizações inscritos no zero emissões de configurações, bloquear esta página.
- **URL de experiência de executar primeiro indique a localização** (apenas Windows 10 Mobile): Introduza o URL que aponta para o ficheiro XML que contém os URLs de página de execução primeiro. Por exemplo, introduza `https://www.contoso.com/sites.xml`.

- **Atualize o browser após o tempo de inatividade**: Introduza o número de minutos de inatividade até o navegador é atualizado, de 0-1440 minutos. A predefinição é `5` minutos. Quando definido como `0` (zero), o navegador não atualiza após inatividade.

  Esta definição só está disponível quando em execução no [(quiosque de aplicação única) de Navegação InPrivate pública](#use-microsoft-edge-kiosk-mode).

- **Permitir pop-ups** (apenas ambiente de trabalho): **Sim** (predefinição) permite que o pop-ups do browser. **Não** impede que as janelas pop-up no browser.
- **Enviar tráfego da intranet para o Internet Explorer** (apenas ambiente de trabalho): **Sim** permite que os utilizadores abram sites da intranet no Internet Explorer em vez do Microsoft Edge. Esta definição é para fins de compatibilidade. **Não** (predefinição) permite que os utilizadores utilizem o Microsoft Edge.
- **Localização de lista de sites de modo de empresa** (apenas ambiente de trabalho): Introduza o URL que aponta para o ficheiro XML que contém uma lista de sites que abrem no modo empresarial. Os utilizadores não é possível alterar o dessa lista. Por exemplo, introduza `https://www.contoso.com/sites.xml`.
- **Mensagem ao abrir sites no Internet Explorer**: Utilize esta definição para configurar o Microsoft Edge para mostrar uma notificação antes de um site é aberta no Internet Explorer 11. As opções são:
  - **Não Mostrar mensagem**: É utilizado o comportamento padrão do sistema operacional, que não pode mostrar uma mensagem.
  - **Mostrar mensagem que site é aberta no Internet Explorer 11**: Mostre a mensagem ao abrir sites no IE. Os sites abertos no IE. 
  - **Mostrar mensagem com a opção de abrir sites no Microsoft Edge**: Mostre a mensagem ao abrir sites no Edge. A mensagem inclui uma **continue a utilizar no Microsoft Edge** ligar para os utilizadores possam escolher o Microsoft Edge em vez do IE.

  > [!IMPORTANT]
  > Esta definição exige que utilize o **localização de lista de sites de modo de empresa** definição, o **enviar tráfego da intranet para o Internet Explorer** definição ou ambas as definições.

- **Permitir que a lista de compatibilidade Microsoft**: **Sim** (predefinição) permite o uso de uma lista de compatibilidade da Microsoft. **Não** impede que a lista de compatibilidade Microsoft no Microsoft Edge. Esta lista da Microsoft Ajuda Microsoft Edge apresente corretamente os sites com problemas de compatibilidade conhecidos.
- **Pré-carregar páginas de início e de página novo separador**: **Sim** (predefinição) utiliza o comportamento padrão de sistema operacional, que pode ser pré-carregar essas páginas. Pré-carregamento minimiza o tempo para iniciar o Microsoft Edge e carregar novas guias. **Não** impede o pré-carregamento de páginas de início e a nova página de separador do Microsoft Edge.
- **Iniciará páginas de início e de página novo separador**: **Sim** (predefinição) utiliza o comportamento padrão de sistema operacional, que pode ser iniciará a essas páginas. Pré-início ajuda o desempenho do Microsoft Edge e minimiza o tempo necessário para iniciar o Microsoft Edge. **Não** impede que o Microsoft Edge previamente iniciar as páginas de início e a nova página de separador.

Selecione **OK** para guardar as alterações.

### <a name="favorites-and-search"></a>Favoritos e pesquisar

- **Mostrar barra de Favoritos**: Escolha o que acontece na barra de Favoritos em qualquer página do Microsoft Edge. As opções são:
  - **No início e de novas páginas de separador**: Mostra os favoritos, barra quando o Microsoft Edge é iniciado e em todas as páginas de separador. Os utilizadores finais podem alterar esta definição.
  - **Em todas as páginas**: Mostra a barra de Favoritos em todas as páginas. Os utilizadores finais não é possível alterar esta definição.
  - **Oculto**: Oculta a barra de Favoritos em todas as páginas. Os utilizadores finais não é possível alterar esta definição.
- **Permitir alterações aos Favoritos**: **Sim** (predefinição) utiliza a predefinição do sistema operacional, o que permite aos usuários alterar a lista. **Não** impede que os utilizadores finais de adicionarem, importar, classificação ou editar a lista de Favoritos.
  - **Lista de Favoritos**: Adicione uma lista de URLs para o ficheiro de Favoritos. Por exemplo, adicionar `http://contoso.com/favorites.html`.
- **Sincronizar favoritos entre browsers da Microsoft** (apenas ambiente de trabalho): **Sim** força do Windows para sincronizar favoritos entre o Internet Explorer e o Microsoft Edge. Adições, eliminações, modificações e alterações de ordem nos favoritos são partilhadas entre browsers.  **Não** (predefinição) usa o padrão de SO, o que poderá que os utilizadores para sincronizar favoritos entre browsers.
- **Motor de busca predefinido**: Escolha o motor de busca predefinido no dispositivo. Os utilizadores finais podem alterar este valor em qualquer altura. As opções são:
  - Mecanismo de pesquisa nas definições do Microsoft Edge de cliente
  - Bing
  - Google
  - Yahoo
  - Valor personalizado: Na **URL Xml do OpenSearch**, introduza um URL HTTPS com o arquivo XML que inclui o nome abreviado e o URL para o motor de busca, no mínimo. Por exemplo, introduza `https://www.contoso.com/opensearch.xml`.
- **Mostrar sugestões de pesquisa**: **Sim** (predefinição) permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa na barra de endereço. **Não** impede que esta funcionalidade.
- **Permitir alterações para o mecanismo de pesquisa**: **Sim** (predefinição) permite aos utilizadores adicionar novos mecanismos de pesquisa ou alterar o motor de busca predefinido no Microsoft Edge. Escolher **não** impedir os utilizadores de personalizar o motor de busca.

  Esta definição só está disponível quando em execução no [modo Normal (quiosque de várias aplicações)](#use-microsoft-edge-kiosk-mode).

Selecione **OK** para guardar as alterações.

### <a name="privacy-and-security"></a>Privacidade e segurança

- **Permitir a Navegação InPrivate**: **Sim** (predefinição) permite a Navegação InPrivate no Microsoft Edge. Depois de fechar todas as guias InPrivate, o Microsoft Edge elimina os dados de navegação do dispositivo. **Não** impede que os utilizadores finais abrir sessões de Navegação InPrivate.
- **Guardar o histórico de navegação**: **Sim** (predefinição) permitir guardar o histórico de navegação no Microsoft Edge. **Não** impede a guardar o histórico de navegação.
- **Limpar dados de navegação à saída** (apenas ambiente de trabalho): **Sim** limpa o histórico e dados de navegação quando o utilizador sai do Microsoft Edge. **Não** (predefinição) usa o padrão de sistema operacional, o que pode colocar em cache os dados de navegação.
- **Sincronizar as definições do browser entre dispositivos do utilizador**: Escolha como pretende sincronizar as definições do browser entre dispositivos. As opções são:
  - **Permitir**: Permitir a sincronização de definições do browser Microsoft Edge entre dispositivos do utilizador
  - **Bloquear e ativar a substituição de utilizador**: Bloquear a sincronização de definições do browser Microsoft Edge entre dispositivos do utilizador. Os utilizadores podem substituir esta definição.
  - **Bloco**: Bloquear a sincronização de configuração de browser do Microsoft Edge entre dispositivos de utilizadores. Os utilizadores não podem substituir esta definição.

Quando é selecionado "bloquear e ativar a substituição de utilizador", o utilizador pode ignorar a designação de administrador.

- **Permitir Gestor de palavra-passe**: **Sim** (predefinição) permite que o Microsoft Edge utilizar automaticamente o Gestor de palavra-passe, que permite aos utilizadores guardar e gerir palavras-passe no dispositivo. **Não** impede que o Microsoft Edge com o Gestor de palavra-passe.
- **Cookies**: Escolha como os cookies são processados no navegador da web. As opções são:
  - **Permitir**: Cookies são armazenados no dispositivo.
  - **Bloquear todos os cookies**: Cookies não são armazenados no dispositivo.
  - **Bloquear apenas cookies de terceiros**: Os cookies de parceiro de terceiros ou não são armazenados no dispositivo.
- **Permitir Preenchimento automático em formulários**: **Sim** (predefinição) permite que os utilizadores alterem as definições no browser e preencher os campos de formulário automaticamente. **Não** desativa a funcionalidade de preenchimento automático no Microsoft Edge.
- **Enviar cabeçalhos de realizar rastreio não**: **Sim** envia cabeçalhos para não realizar-rastreio em Web sites que pedem informações de controlo (recomendada). **Não** (predefinição) não enviar cabeçalhos que permite que os Web sites controlar o utilizador. Pode configurar o utilizador.
- **Mostrar o endereço IP de localhost do WebRTC**: **Sim** (predefinição) permite que o endereço IP de localhost dos utilizadores a serem apresentados ao efetuar chamadas telefónicas utilizando esse protocolo. **Não** impede que o endereço IP de localhost dos utilizadores a ser mostrada. 
- **Permitir recolha de dados do mosaico dinâmico**: **Sim** (predefinição) permite que o Microsoft Edge recolher informações de quadros ao vivo afixado no menu Iniciar. **Não** impede que a recolha destas informações, que podem fornecer aos utilizadores uma experiência limitada.
- **Utilizador pode ignorar erros de certificado**: **Sim** (predefinição) permite aos utilizadores aceder a sites que têm erros de Secure Sockets Layer/Transport Layer Security (SSL/TLS). **Não** (recomendado para maior segurança) impede que os utilizadores de aceder ao Web sites com erros SSL ou TLS.

Selecione **OK** para guardar as alterações.

### <a name="additional"></a>Adicionais

- **Permitir browser Microsoft Edge** (apenas móvel): **Sim** (predefinição) permite o uso do browser Microsoft Edge no dispositivo móvel. **Não** impede a utilizar o Microsoft Edge no dispositivo. Se escolher **não**, as outras definições individuais só se aplicam a área de trabalho.
- **Permitir que a lista suspensa de barra de endereço**: **Sim** (predefinição) permite que o Microsoft Edge Mostrar a barra de endereços pendente com uma lista de sugestões. **Não** interrompe o Microsoft Edge de mostrar uma lista de sugestões numa lista pendente, quando escreve. Quando definido como **não**,:
  - Ajudar a minimizar a largura de banda de rede entre o Microsoft Edge e os serviços da Microsoft.
  - Desativar a **Mostrar sugestões de pesquisa e o site enquanto digito** no Microsoft Edge > definições.
- **Permitir modo de ecrã inteiro**: **Sim** (predefinição) permite que o Microsoft Edge para o modo de ecrã inteiro de utilização, que mostra apenas o conteúdo da web e oculta a interface do Usuário do Microsoft Edge. **Não** impede que o modo de ecrã inteiro no Microsoft Edge.
- **Permitir sobre a página de sinalizadores**: **Sim** (predefinição) utiliza a predefinição de sistema operacional, que pode permitir que a aceder a `about:flags` página. O `about:flags` página permite aos usuários alterar as definições de programador e ativar funcionalidades experimentais. **Não** impede que os utilizadores finais acedam a `about:flags` página no Microsoft Edge.
- **Permitir ferramentas de programação**: **Sim** (predefinição) permite que os utilizadores utilizem as ferramentas de desenvolvedor F12 para criar e depurar páginas da web por predefinição. **Não** impede que os utilizadores finais com as ferramentas de desenvolvedor F12.
- **Permitir que o JavaScript**: **Sim** (predefinição) permite que scripts, como Javascript, sejam executados no browser Microsoft Edge. **Não** impede que os scripts de Java no browser em execução.
- **Utilizador pode instalar extensões**: **Sim** (predefinição) permite que os utilizadores finais instalarem as extensões do Microsoft Edge no dispositivo. **Não** impede a instalação.
- **Permitir o sideload das extensões de desenvolvedor**: **Sim** (predefinição) utiliza a predefinição do sistema operacional, o que poderá permitir o sideload. Sideload instala e executa extensões não verificadas. **Não** impede que o Microsoft Edge sideload usando o **carregam extensões** funcionalidade. Ele não impede as extensões de sideload usando outras formas, como o PowerShell.
- **Necessário extensões**: Escolha quais as extensões que não podem ser desativadas pelos usuários finais na Microsoft Edge. Introduza os nomes da família de pacote e selecione **adicionar**. [Localizar um nome de família de pacotes (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) fornece algumas diretrizes.

  Também pode **importação** um ficheiro CSV que inclui os nomes da família de pacotes. Ou, **exportar** introduzir nomes da família do pacote.

Selecione **OK** para guardar as alterações.

## <a name="network-proxy"></a>Proxy de rede

Utilizam estas definições a [NetworkProxy política CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), que também apresenta uma lista de edições suportadas do Windows.

- **Detetar automaticamente as definições de proxy**: **Bloco** desativa o dispositivo de detetar automaticamente um script de configuração (PAC) de automática do proxy. **Não configurado** (predefinição) habilita esse recurso. Quando ativada, o dispositivo tenta localizar o caminho para um script PAC.
- **Utilizar script de proxy**: Escolher **permitir** a inserir um caminho para o script de PAC para configurar o servidor proxy. **Não configurado** (predefinição) não permite que insira o URL para um script de PAC.
  - **URL de endereço do script de configuração**: Introduza o URL de um script de PAC que pretende utilizar para configurar o servidor proxy.
- **Utilizar um servidor manual proxy**: Escolher **permitir** para introduzir manualmente o nome ou endereço IP e número da porta TCP de um servidor proxy. **Não configurado** (predefinição) não permite que inserir manualmente os detalhes de um servidor proxy.
  - **Endereço**: Introduza o nome ou endereço IP do servidor proxy.
  - **Número de porta**: Introduza o número de porta do servidor proxy.
  - **Exceções de proxy**: Introduza os URLs que não tem de utilizar o servidor proxy. Utilize um ponto e vírgula para separar cada item.
  - **Ignorar servidor proxy para endereço local**: **Não configurado** (predefinição) impede a utilização de um servidor de proxy para endereços locais na sua intranet. **Permitir** utiliza um servidor proxy para endereços locais.

Selecione **OK** para guardar as alterações.

## <a name="password"></a>Palavra-passe

Utilizam estas definições a [DeviceLock política CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), que também apresenta uma lista de edições suportadas do Windows.

- **Palavra-passe**: **Exigir** que o utilizador final introduza uma palavra-passe para aceder ao dispositivo. **Não configurado** (predefinição) permite o acesso ao dispositivo sem uma palavra-passe.
  - **Tipo obrigatório de palavra-passe**: Escolha o tipo de palavra-passe. As opções são:
    - **Não configurado**: Palavra-passe pode incluir letras e números.
    - **Numérica**: Palavra-passe tem de ser apenas números.
    - **Alfanumérica**: Palavra-passe tem de ser uma combinação de números e letras.
  - **Comprimento mínimo da palavra-passe**: Introduza o número mínimo ou carateres necessários, a partir de 4 a 16. Por exemplo, introduza `6` para exigir pelo menos seis caracteres de comprimento de palavra-passe.
  - **Número de falhas de início de sessão antes de apagar o dispositivo**: Introduza o número de falhas de autenticação permitidas antes do dispositivo é apagado, a partir de 1 a 11. `0` (zero), pode desativar a funcionalidade de eliminação do dispositivo.

    Esta definição não tem um impacto diferente, dependendo da edição. Para obter detalhes específicos, consulte a [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Máximo de minutos de inatividade até o ecrã ser bloqueado**: Introduza o período de tempo que um dispositivo tem de estar inativo antes do ecrã ser bloqueado.
  - **Expiração da palavra-passe (dias)** : Introduza o período de tempo em dias quando a palavra-passe do dispositivo deve ser alterada, de 1-365. Por exemplo, introduza `90` para expirar a palavra-passe após 90 dias.
  - **Impedir a reutilização de palavras-passe anteriores**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizada, a partir de 1 a 24. Por exemplo, introduza `5` para que os utilizadores não é possível definir uma nova palavra-passe para a palavra-passe atual ou qualquer uma das suas palavras-passe anteriores quatro.
  - **Exigir palavra-passe quando o dispositivo regressa do Estado de inatividade** (Mobile e Holographic): Escolher **requerem** para que os utilizadores tem de introduzir uma palavra-passe para desbloquear o dispositivo após inatividade. **Não configurado** (predefinição) não exige um PIN ou palavra-passe quando o dispositivo sai de um estado inativo.
  - **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como `1234` ou `1111`. Defina como **não configurado** (predefinição) para permitir aos utilizadores criar palavras-passe como `1234` ou `1111`. Esta definição também permite ou bloqueia a utilização de palavras-passe por imagem do Windows.
- **Encriptação automática durante a AADJ**: **Bloco** impede que a encriptação de dispositivos de disco BitLocker automática quando o dispositivo está preparado para a primeira utilização, quando o dispositivo estiver associado ao Azure AD. **Não configurado** (predefinição) utiliza a predefinição do sistema operativo, o que pode ativar a encriptação. Mais diante [criptografia de dispositivo de disco BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [Segurança/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **Política de Federal Information Processing Standard (FIPS)** : **Permitir** utiliza a política de Federal Information Processing Standard (FIPS), que é um Governo dos E.U.A. standard para a encriptação, hash e assinatura. **Não configurado** (predefinição) utiliza a predefinição do sistema operativo, o que não usa o FIPS.

  [Criptografia/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Autenticação do dispositivo Windows Hello**: **Permitir** os utilizadores utilizem um Windows Hello dispositivo complementar, como um telemóvel, a banda de adequação ou o dispositivo de IoT, para iniciar sessão no computador Windows 10. **Não configurado** (predefinição) utiliza a predefinição do sistema operativo, o que pode impedir que os dispositivos Windows Hello complementar a autenticação com o Windows.

  [Autenticação/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Início de sessão da Web**: Permite o início de sessão do Windows no suporte para fornecedores de federado não ADFS (Serviços de Federação do Active Directory), tais como SAML Security Assertion Markup Language (). SAML utiliza tokens seguras que fornecem a experiência de navegadores da web um início de sessão único (SSO). As opções são:

  - **Não configurado** (predefinição): Utiliza a predefinição do sistema operativo no dispositivo.
  - **Ativado**: O provedor de credenciais da Web está ativado para início de sessão.
  - **Desativado**: O provedor de credenciais da Web está desativado para início de sessão.

  [Autenticação/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Preferencial de domínio de inquilino do Azure AD**: Introduza um nome de domínio existente na sua organização do Azure AD. Quando os utilizadores neste domínio iniciam sessão, não precisam de se escrever o nome de domínio. Por exemplo, introduza `contoso.com`. Os utilizadores a `contoso.com` domínio possam iniciar sessão com o respetivo nome de utilizador, tais como `abby`, em vez de `abby@contoso.com`.

  [Autenticação/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

Selecione **OK** para guardar as alterações.

## <a name="per-app-privacy-exceptions"></a>Exceções de privacidade por aplicação

Pode adicionar aplicações que devem ter um comportamento de privacidade diferente do define na "Privacidade predefinida".

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
- **Dispositivos fidedignos**: Escolha se esta aplicação pode utilizar dispositivos fidedignos. Dispositivos fidedignos são hardware que já ligou ou hardware que é fornecido com o dispositivo. Por exemplo, utilize o TVs, projetores etc., como dispositivos fidedignos.
- **Comentários e diagnóstico**: Defina se esta aplicação pode aceder a informações de diagnóstico.
- **Sincronização com dispositivos**: Escolha se esta aplicação pode partilhar e sincronizar informações com dispositivos sem fios que não sejam emparelham especificamente com o dispositivo automaticamente.

Selecione **OK** para guardar as alterações.

## <a name="personalization"></a>Personalização

Utilizam estas definições a [CSP de política de personalização](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), que também apresenta uma lista de edições suportadas do Windows.

- **URL da imagem de fundo (apenas ambiente de trabalho)** : Introduza o URL para uma imagem no formato jpg,. JPEG ou. PNG que pretende utilizar como a imagem de fundo de ambiente de trabalho Windows. Os utilizadores não podem alterar a imagem. Por exemplo, introduza `https://contoso.com/logo.png`.

Selecione **OK** para guardar as alterações.

## <a name="printer"></a>Impressora

- **Impressoras**: Lista de impressoras locais que foram adicionados.
- **Impressora predefinida**: Defina a impressora predefinida.
- **Acesso de utilizador para adicionar novas impressoras**: Permitir ou bloquear a utilização de impressoras locais.

Selecione **OK** para guardar as alterações.

## <a name="privacy"></a>Privacidade

Utilizam estas definições a [CSP de política de privacidade](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), que também apresenta uma lista de edições suportadas do Windows.

- **Personalização de entrada**: **Bloco** impede que impede que usando a voz para ditado e para comunicar com o Cortana e outras aplicações que utilizam o reconhecimento de fala baseados na cloud da Microsoft. Está desativada e os utilizadores não é possível ativar o reconhecimento de voz online com as definições. **Não configurado** (predefinição) permite aos utilizadores escolher. Se permitir estes serviços, a Microsoft poderá recolher dados de voz para melhorar o serviço.
- **Aceitação automática das solicitações de consentimento de utilizador de emparelhamento e privacidade**: Escolher **permitir** para que o Windows podem aceitar automaticamente emparelhamento e privacidade as mensagens de consentimento ao executar as aplicações. **Não configurado** (predefinição) impede que a aceitação automática da janela de consentimento de utilizador de emparelhamento e privacidade ao abrir aplicações.
- **Publicar as atividades do utilizador**: **Bloco** impede que as experiências compartilhadas e deteção de recursos recentemente utilizados no feed de atividades. **Não configurado** (predefinição) habilita esse recurso para que as aplicações podem publicar as atividades de utilizador final.
- **Apenas atividades locais**: **Bloco** impede que as experiências compartilhadas e a deteção de recursos recentemente utilizados no comutador de tarefas, com base na atividade local. **Não configurado** (predefinição) habilita esse recurso.

Pode configurar as informações que podem aceder a todas as aplicações no dispositivo. Além disso, definir exceções de uma base por aplicação a utilizar **exceções de privacidade por aplicação**.

Selecione **OK** para guardar as alterações.

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
- **Dispositivos fidedignos**: Escolha se esta aplicação pode utilizar dispositivos fidedignos. Dispositivos fidedignos são hardware que já ligou ou hardware que vem com o dispositivo. Por exemplo, utilize o TVs, projetores etc., como dispositivos fidedignos.
- **Comentários e diagnóstico**: Escolha se esta aplicação pode aceder a informações de diagnóstico.
- **Sincronização com dispositivos** – defina se esta aplicação pode partilhar e sincronizar automaticamente informações com dispositivos sem fios que não sejam emparelhados especificamente com o PC, tablet ou telefone.

Selecione **OK** para guardar as alterações.

## <a name="projection"></a>Projeção

Utilizam estas definições a [WirelessDisplay política CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), que também apresenta uma lista de edições suportadas do Windows.

- **Entrada de utilizador de recetores de ecrã sem fios**: **Bloco** impede a intervenção do utilizador de recetores de ecrã sem fios. **Não configurado** (predefinição) permite que um ecrã sem fios enviar o teclado, mouse, caneta e a entrada de volta para o dispositivo de origem por toque.
- **Projeção para este PC**: **Bloco** impede outros dispositivos de localizar o dispositivo para projeção. **Não configurado** (predefinição) permite que o dispositivo ser detetável e pode projeto para o dispositivo acima do ecrã de bloqueio.
- **Exigir PIN para emparelhamento**: Escolher **requerem** sempre solicitar um PIN ao ligar a um dispositivo de projeção. **Não configurado** (predefinição), não precisa de um PIN emparelhar o dispositivo a um dispositivo de projeção.

Selecione **OK** para guardar as alterações.

## <a name="reporting-and-telemetry"></a>Relatórios e telemetria

- **Partilhar dados de utilização**: Escolha o nível de dados de diagnóstico que são submetidos. As opções são:
  - **Não configurado**: Não existem dados são partilhados.
  - **Segurança**: Informações necessárias para ajudar a manter o Windows mais seguro, incluindo dados sobre as definições de componente de telemetria e experiência do usuário conectado, a ferramenta de remoção de Software Malicioso e o Windows Defender.
  - **Básico**: Informações básicas do dispositivo, incluindo dados relacionados com a qualidade, compatibilidade de aplicativos, dados de utilização de aplicações e dados de nível de segurança.
  - **Avançada**: Informações adicionais, incluindo: como o Windows, Windows Server, System Center e aplicações são utilizadas, como executar, dados de confiabilidade avançada e dados de Basic e os níveis de segurança.
  - **Total**: Todos os dados necessários para identificar e ajudar a corrigir problemas, além de dados entre os níveis de segurança, básico e avançado.

  [Sistema/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Enviar dados para o Microsoft 365 Analytics de navegação do Microsoft Edge**: Para utilizar esta funcionalidade, defina o **partilhar dados de utilização** configurações para **avançado** ou **completa**. Esta funcionalidade controla que dados Microsoft Edge envia para o Microsoft 365 Analytics dos dispositivos da empresa com um ID comercial configurado. As opções são:
  - **Não configurado**: Utiliza o padrão de sistema operacional, o que não pode enviar quaisquer dados de histórico de navegação
  - **Enviar apenas dados de intranet**: Permite ao administrador enviar o histórico de dados de intranet
  - **Enviar apenas dados de internet**: Permite ao administrador enviar o histórico de dados da internet
  - **Enviar dados de intranet e internet**: Permite ao administrador enviar o histórico de dados de intranet e internet

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Servidor de proxy da telemetria**: Introduza o nome de domínio completamente qualificado (FQDN) ou o endereço IP de um servidor proxy para reencaminhar pedidos de telemetria, através de uma ligação de Secure Sockets Layer (SSL) e experiências do usuário conectado. O formato para esta definição é *servidor*:*porta*. Se o proxy nomeado falhar ou se um proxy não é introduzido quando ativar esta política, os dados de telemetria e experiências de utilizador ligado não são enviados e permanecem no dispositivo local.

  Formatos de exemplo:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [Sistema/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Selecione **OK** para guardar as alterações.

## <a name="search"></a>Pesquisa

Utilizam estas definições a [pesquisar política CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), que também apresenta uma lista de edições suportadas do Windows. 

- **Pesquisa segura (apenas móvel)** : Controle a forma como a Cortana filtra o conteúdo para adultos nos resultados da pesquisa. As opções são:
  - **Definido pelo utilizador**: Permitir que os utilizadores finais escolher as suas próprias definições.
  - **Strict**: Mais alta filtragem de conteúdos para adultos.
  - **Moderado**: Filtragem moderada de conteúdos para adultos. Os resultados de pesquisa válidos não são filtrados.
- **Mostrar os resultados da web na procura**: Quando definido como **bloco**, os utilizadores não consegue pesquisar e os resultados da web não são apresentados no Search. **Não configurado** (predefinição) permite aos utilizadores pesquisar a web e os resultados são apresentados no dispositivo.

Selecione **OK** para guardar as alterações.

## <a name="start"></a>Iniciar,

Utilizam estas definições a [começar a política de CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), que também apresenta uma lista de edições suportadas do Windows.  

- **Esquema do menu Iniciar**: Substituir o layout de início padrão e personalizar o menu Iniciar nos dispositivos de ambiente de trabalho. Carrega um ficheiro XML que inclui suas personalizações, incluindo a ordem que as aplicações forem apresentadas, e muito mais. Os utilizadores não é possível alterar o esquema do menu Iniciar que introduzir.
- **Afixar sites a mosaicos no menu Iniciar**: Importar imagens a partir do Microsoft Edge, que são apresentados como ligações no menu Iniciar do Windows para dispositivos de ambiente de trabalho.
- **Remover aplicações da barra de tarefas**: **Bloco** impede que os utilizadores de remover aplicações a partir da barra de tarefas. **Não configurado** (predefinição) permite aos utilizadores remover aplicações a partir da barra de tarefas.
- **Mudança rápida de utilizador**: **Bloco** impede a troca entre os utilizadores que tenham sessão iniciados em simultâneo sem fazer logoff. **Não configurado** (predefinição) mostra a **mudar de utilizador** no mosaico do utilizador.
- **Aplicações mais utilizadas**: **Bloco** oculta as aplicações mais utilizadas de mostrar no menu Iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (predefinição) mostra aplicações a mais utilizadas.
- **Aplicações adicionadas recentemente**: **Bloco** oculta as aplicações recentemente adicionadas de mostrar no menu Iniciar. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (predefinição) mostra as aplicações adicionadas recentemente, no menu Iniciar.
- **Iniciar modo de ecrã**: Escolha a forma como é apresentado o ecrã de início. As opções são:
  - **Definido pelo utilizador**: Não forçar o tamanho do início. Os utilizadores podem definir o tamanho.
  - **Ecrã inteiro**: Força um tamanho de ecrã inteiro de início.
  - **Ecrã não inteiro**: Forçar tamanho de não-ecrã inteiro do início.
- **Recentemente, abrir itens em listas de atalhos**: **Bloco** oculta recentes listas de atalhos do que está a ser mostrada no menu Iniciar e barra de tarefas. Também desativa o seletor correspondente na aplicação Definições. **Não configurado** (predefinição) mostra itens abertos recentemente nas listas de atalhos.
- **Lista de aplicações**: Escolha a forma como são apresentadas todas as listas de aplicações. As opções são:
  - **Definido pelo utilizador**: Nenhuma definição é forçada. Os usuários escolher a forma como a lista de aplicações é apresentada no dispositivo.
  - **Fechar**: Oculta todas as listas de aplicações.
  - **Fechar e desativar a aplicação de definições**: Ocultar todas as listas de aplicações e desativar **Mostrar a lista de aplicações no menu Iniciar** na aplicação definições.
  - **Remove e desativa a aplicação de definições**: Ocultar todas as listas de aplicações, todas as aplicações botão Remover e desativar **Mostrar a lista de aplicações no menu Iniciar** na aplicação definições.
- **Botão de energia**: **Bloco** oculta o botão de energia do que mostra no menu Iniciar. **Não configurado** (predefinição) mostra o botão de energia.
- **Mosaico de utilizador**: **Bloco** oculta o mosaico de utilizador de mostrar no menu Iniciar. **Não configurado** mostra o mosaico de utilizador (predefinição) e também define as seguintes definições:
  - **Bloqueio**: **Bloco** oculta a **bloqueio** opção de mostrar no mosaico de utilizador no menu Iniciar. **Não configurado** (predefinição) mostra a **bloqueio** opção.
  - **Terminar sessão**: **Bloco** oculta a **terminar sessão** opção de mostrar no mosaico de utilizador no menu Iniciar. **Não configurado** (predefinição) mostra a **terminar sessão** opção.
- **Encerrar**: **Bloco** oculta a **atualização e encerre** e **Encerrar** opções de mostrar no botão de energia no menu Iniciar. **Não configurado** (predefinição) mostra essas opções.
- **Modo de suspensão**: **Bloco** oculta a **suspensão** opção de mostrar no botão de energia no menu Iniciar. **Não configurado** (predefinição) mostra essa opção.
- **Hibernar**: **Bloco** oculta a **Hibernar** opção de mostrar no botão de energia no menu Iniciar. **Não configurado** (predefinição) mostra essa opção.
- **Mudar de conta**: **Bloco** oculta a **mudar de conta** de mostrar o utilizador mosaico no menu Iniciar. **Não configurado** (predefinição) mostra essa opção.
- **Opções de reinício**:  **Bloco** oculta a **atualizar e reiniciar** e **reiniciar** opções de mostrar no botão de energia no menu Iniciar. **Não configurado** (predefinição) mostra essas opções.
- **Documentos em Iniciar**: Ocultar ou mostrar a pasta documentos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Transferências em Iniciar**: Ocultar ou mostrar a pasta transferências no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Explorador de ficheiros em Iniciar**: Ocultar ou mostrar o Explorador de ficheiros no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Grupo doméstico em Iniciar**: Ocultar ou mostrar o atalho grupo doméstico no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Música em Iniciar**: Ocultar ou mostrar a pasta Música no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Rede em Iniciar**: Ocultar ou mostrar a rede no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Pasta pessoal em Iniciar**: Ocultar ou mostrar a pasta pessoal no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Imagens em Iniciar**: Ocultar ou mostrar a pasta de imagens no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Definições em Iniciar**: Ocultar ou mostrar o atalho definições no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.
- **Vídeos em Iniciar**: Ocultar ou mostrar a pasta dos vídeos no menu Iniciar do Windows. As opções são:
  - **Não configurado** (predefinição): Nenhuma definição é forçada. Os utilizadores optar por mostrar ou ocultar o atalho.
  - **Ocultar**: O atalho está oculta e desativa a definição na aplicação definições.
  - **Mostrar**: O atalho é mostrado e desativa a definição na aplicação definições.

Selecione **OK** para guardar as alterações.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para o Microsoft Edge**: **Exigir** desativa o Windows Defender SmartScreen e impedir que os utilizadores ativá-la. **Não configurado** (padrão) ativa o SmartScreen. Ajuda a proteger os usuários contra potenciais ameaças e impedir que os utilizadores desligá-lo.

  Microsoft Edge utiliza o Windows Defender SmartScreen (ativado) para proteger os usuários contra potenciais atos fraudulentos de phishing e software malicioso.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Acesso a site malicioso**: **Bloco** impede que os utilizadores ignorem os avisos do filtro Smartsceen do Windows Defender e bloqueia-los de aceder ao site. **Não configurado** (predefinição) permite aos utilizadores ignorar os avisos e continuar para o site.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Transferência de ficheiros não verificados**: **Bloco** impede que os utilizadores ignorem os avisos do filtro do Windows Defender SmartScreen e impeça-os de transferir ficheiros não verificados. **Não configurado** (predefinição) permite aos utilizadores ignorar os avisos e continuar a transferir os ficheiros não verificados.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

Selecione **OK** para guardar as alterações.

## <a name="windows-spotlight"></a>Destaque do Windows

Utilizam estas definições a [experiência de política de CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), que também apresenta uma lista de edições suportadas do Windows.

- **Destaque do Windows**: **Bloco** funcionalidades relacionadas com a desliga o destaque do Windows no ecrã de bloqueio, sugestões do Windows, funcionalidades do consumidor Microsoft e outros. Se o seu objetivo é minimizar o tráfego de rede a partir de dispositivos, defina esta opção como **bloco**. **Não configurado** (predefinição) permite o Windows em destaque funcionalidades e podem ser controladas pelos usuários finais. Quando ativada, também pode permitir ou bloquear as seguintes definições:

  - **Destaque do Windows no ecrã de bloqueio**: **Bloco** impede o destaque do Windows de mostrar as informações no ecrã de bloqueio do dispositivo. **Não configurado** (predefinição) habilita esse recurso.
  - **Sugestões de terceiros no destaque do Windows**: **Bloco** impede o destaque do Windows de sugerir conteúdos que não sejam publicados pela Microsoft. **Não configurado** (predefinição) permite que a aplicação e conteúdos sugestões de editores de software de parceiro em funcionalidades do destaque do Windows, como em destaque do ecrã de bloqueio, sugestões de aplicações no menu Iniciar e dicas do Windows.
  - **Funcionalidades do consumidor**: **Bloco** se desligar experiências normalmente destinadas a consumidores apenas, tais como sugestões de início, notificações de associação, pós-cópia fora da instalação de aplicação de experiência de caixa, e mosaicos de redirecionamento. **Não configurado** (predefinição) permite estas funcionalidades.
  - **Dicas do Windows**: **Bloco** desativa sugestões pop-up do Windows. **Não configurado** (predefinição) permite que as Dicas do Windows mostrar.
  - **Destaque do Windows no Centro de ação**: **Bloco** impede notificações de destaque do Windows de mostrar no Centro de ação. **Não configurado** (predefinição) pode mostrar notificações no Centro de ação que sugerem as aplicações ou funcionalidades para ajudar os utilizadores sejam mais produtivos no Windows.
  - **Personalização do destaque do Windows**: **Bloco** impede que o Windows utilize dados de diagnóstico para fornecer experiências personalizadas ao utilizador. **Não configurado** (predefinição) permite que a Microsoft utilizar dados de diagnóstico para fornecer recomendações personalizadas, dicas e ofertas para personalizar o Windows para as necessidades do usuário.
  - **Experiência de boas-vindas Windows**: **Bloco** funcionalidade Experiência de desliga o destaque do Windows boas-vindas do Windows. A experiência de boas-vindas do Windows não mostrará quando existem atualizações e alterações ao Windows e respetivas aplicações. **Não configurado** (predefinição) permite Windows bem-vindo a experiência que mostra informações sobre funcionalidades novas ou atualizadas.

Selecione **OK** para guardar as alterações.

## <a name="windows-defender-antivirus"></a>Antivírus do Windows Defender

Utilizam estas definições a [CSP de política de defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), que também apresenta uma lista de edições suportadas do Windows.

- **Monitorização em tempo real**: **Ativar** impede que a análise em tempo real de software maligno, spyware e outro software indesejável. **Não configurado** (predefinição) permite que esta funcionalidade.
- **Monitorização de comportamento**: **Ativar** impede que o Defender verifique a existência de determinados padrões conhecidos de atividade suspeita nos dispositivos. **Não configurado** (predefinição) permite a monitorização de comportamento do Windows Defender.
- **Network Inspection System (NIS)** : NIS ajuda a proteger os dispositivos contra exploits baseados na rede. Utiliza as assinaturas de vulnerabilidades conhecidas do Microsoft Endpoint Protection Center para ajudar a detetar e bloquear tráfego malicioso.
- **Analisar todas as transferências**: Controla se o Defender analisa todos os ficheiros transferidos da Internet.
- **Analisar scripts carregados em browsers da Microsoft**: **Não configurado** (predefinição) permite que o Defender analise scripts que são utilizados no Internet Explorer. **Ativar** impede que esta análise.
- **Acesso do utilizador final ao Defender**: **Bloco** oculta a interface do usuário do Windows Defender dos utilizadores finais. Todas as notificações do Windows Defender também são suprimidas. **Não configurado** (predefinição) permite o acesso de utilizador para a interface do Usuário do Windows Defender. Quando esta definição for alterada, será aplicada da próxima vez que o PC do utilizador final for reiniciado.
- **Intervalo de atualização de assinatura (em horas)** : Introduza o intervalo de que o Defender verifica para novos ficheiros de assinatura, de 0 e 24. As opções são:

  - **Não configurado** (predefinição)
  - **Não verificar**: Defender não verifica a existência de novos ficheiros de assinatura.
  - **1 a 24**: `1` verifica a cada hora `2` verifica a cada duas horas, `24` verifica todos os dias e assim por diante.
- **Monitorizar a atividade de programas e ficheiros**: Permite que o Defender monitorize a atividade de ficheiros e programas nos dispositivos.
- **Dias antes de eliminar o software malicioso em quarentena**: Continuar a controlar software maligno resolvido para o número de dias que introduzir para que possa verificar manualmente os dispositivos afetados anteriormente. Se definir o número de dias para **0**, software maligno permanece na pasta de quarentena e não são automaticamente removido. Quando definido como `90`, itens de quarentena são armazenados durante 90 dias no sistema e, em seguida, removidos.
- **Limite de utilização da CPU durante uma análise**: Limitar a quantidade de CPU que as análises estão autorizadas a utilizar, partir **1** ao **100**.
- **Verificar arquivos mortos**: **Ativar** impede que o Defender de ficheiros de análise arquivado, tais como ficheiros Zip ou Cab. **Não configurado** (predefinição) permite que esta análise.
- **Analisar mensagens de correio recebidas**: **Ativar** permite que o Defender analise mensagens de e-mail quando chegam no dispositivo. **Não configurado** (predefinição) impede a varredura de e-mail.
- **Analisar unidades amovíveis durante uma análise completa**: **Ativar** impede que as análises completas de unidades amovíveis. **Não configurado** (predefinição) permite que o Defender analise unidades amovíveis, como pens USB.
- **Analisar unidades de rede mapeadas durante uma análise completa**: **Ativar** permite que o Defender analise ficheiros em unidades de rede mapeadas. **Não configurado** (predefinição) impede que a análise completa. Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
- **Analisar ficheiros abertos a partir de pastas de rede**: **Não configurado** (predefinição) permite que o Defender analise ficheiros em unidades de rede partilhadas, tais como ficheiros acedidos a partir de um caminho UNC. **Ativar** impede que esta análise. Se os ficheiros na unidade forem só de leitura, o Defender não conseguirá remover qualquer software maligno encontrado nos mesmos.
- **Proteção da cloud**: **Não configurado** (predefinição) permite que o serviço de proteção ativa Microsoft receba informações sobre a atividade de malware de dispositivos que gere. **Ativar** bloqueia esta funcionalidade.
- **Pedir aos utilizadores antes da submissão de exemplo**: Controles se ficheiros potencialmente maliciosos que possam exigir análise adicional são automaticamente enviados à Microsoft. As opções são:
  - **Não configurado**
  - **Avisar sempre**
  - **Pedir confirmação antes de enviar dados pessoais**
  - **Nunca enviar dados**
  - **Enviar todos os dados sem pedir confirmação**: Os dados são enviados automaticamente

- **Hora a realizar uma análise rápida diária**: Escolha a hora para executar uma análise rápida diária. **Não configurado** não executa uma análise diária. Se pretender mais personalização, configure as **tipo de análise do sistema para executar** definição.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

  > [!WARNING]
  > Esta definição no Intune no portal do Azure pode mostrar um Estado de falha. Este é um bug com a funcionalidade de relatórios. Depois de reproduzir o comportamento e resolução de problemas, o grupo de produto do Intune confirmou que o estado é, na verdade, um sucesso. O relatório de bug será corrigido numa versão futura. Não existem é um ETA atual, à medida que mudam de linhas do tempo. Todas as atualizações para esta funcionalidade sejam anunciadas no [no desenvolvimento do Microsoft Intune](in-development.md).

- **Tipo de análise do sistema para executar**: Agende uma análise de sistema, incluindo o nível de análise e o dia e hora para executar a análise. As opções são:
  - **Não configurado**: Não agendar uma análise de sistema no dispositivo. Os utilizadores finais pode executar manualmente verificações como necessário ou reclamado nos respetivos dispositivos.
  - **Desativar**: Desativa a qualquer sistema de verificação no dispositivo. Escolha esta opção se estiver a utilizar uma solução de parceiro de software antivírus que analisa os dispositivos.
  - **Análise rápida**: Analisa as localizações comuns sempre que exista malware registado, tal como chaves de registro e conhecido pastas de arranque do Windows.
    - **Dia agendado**: Escolha o dia para executar a análise.
    - **Hora agendada**: Escolha a hora para executar a análise.
  - **Análise completa**: Analisa as localizações comuns sempre que exista malware registado e também analisa todos os ficheiros e pastas no dispositivo.
    - **Dia agendado**: Escolha o dia para executar a análise.
    - **Hora agendada**: Escolha a hora para executar a análise.

  Esta definição poderá entrar em conflito com o **hora a realizar uma análise rápida diária** definição. Algumas recomendações:

  - Para executar uma análise rápida diária, configure as **hora a realizar uma análise rápida diária** definição.
  - Para executar uma análise rápida diária e uma análise completa de todas as semanas, em seguida, configure as **hora a realizar uma análise rápida diária**. Definir **tipo de análise do sistema para executar** para uma análise completa com o dia e hora.
  - Não configure o **hora a realizar uma análise rápida diária** definir simultaneamente com o **tipo de análise do sistema para executar** definido como **análise rápida**. Estas definições podem entrar em conflito e poderá não ser executada uma análise.
  - Para executar uma análise rápida toda Terça-feira às 06:00, configure as **tipo de análise do sistema para executar** definição.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

  > [!WARNING]
  > Esta definição no Intune no portal do Azure pode mostrar um Estado de falha. Este é um bug com a funcionalidade de relatórios. Depois de reproduzir o comportamento e resolução de problemas, o grupo de produto do Intune confirmou que o estado é, na verdade, um sucesso. O relatório de bug será corrigido numa versão futura. Não existem é um ETA atual, à medida que mudam de linhas do tempo. Todas as atualizações para esta funcionalidade sejam anunciadas no [no desenvolvimento do Microsoft Intune](in-development.md).

- **Detetar aplicações potencialmente indesejadas**: Escolha o nível de proteção quando o Windows detetar aplicações potencialmente indesejadas. As opções são:
  - **Não configurado** (predefinição): O Windows Defender é desativar a proteção de aplicações potencialmente indesejadas.
  - **Bloco**: O Windows Defender detetar aplicações potencialmente indesejadas e itens detetados são bloqueados. Mostram estes itens no histórico, juntamente com outras ameaças.
  - **Auditoria**: O Windows Defender detetar aplicações potencialmente indesejadas, mas não faz nada. Pode rever informações sobre os aplicativos que do Windows Defender seria tome medidas contra. Por exemplo, procure eventos criados pelo Windows Defender Visualizador de eventos.

  Para obter mais informações sobre aplicações potencialmente indesejadas, veja [detetar e bloquear aplicações potencialmente indesejável](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

- **Ações sobre ameaças de software maligno detetado**: Escolha as ações que o Defender deve executar para cada nível de ameaças Deteta: baixo, moderado, alto e grave. As opções são:
  - **Limpar**
  - **Quarentena**
  - **Remove**
  - **Permitir**
  - **Definido pelo utilizador**
  - **Bloquear**

Selecione **OK** para guardar as alterações.

### <a name="windows-defender-antivirus-exclusions"></a>Exclusões do Antivírus do Windows Defender

- **Ficheiros e pastas a excluir de análises e da proteção em tempo real**: Adiciona um ou mais ficheiros e pastas, como **C:\Path** ou **%ProgramFiles%\Path\filename.exe**, à lista de exclusões. Estes ficheiros e pastas não são incluídos em análises em tempo real ou agendadas.
- **Extensões de ficheiros a excluir de análises e proteção em tempo real**: Adicione uma ou mais extensões de ficheiro, como **jpg** ou **txt**, à lista de exclusões. Os ficheiros com estas extensões não são incluídos em análises em tempo real ou agendadas.
- **Processos a excluir de análises e da proteção em tempo real**: Adicione um ou mais processos do tipo **.exe**, **.com** ou **.scr** à lista de exclusões. Estes processos não são incluídos em análises em tempo real ou agendadas.

Selecione **OK** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

Para obter os detalhes técnicos adicionais de cada definição e quais as edições do Windows suportadas, veja [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Referência de CSP de Políticas do Windows 10)
