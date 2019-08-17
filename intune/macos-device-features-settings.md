---
title: configurações de recurso de dispositivo macOS no Microsoft Intune – Azure | Microsoft Docs
description: Consulte as configurações para configurar dispositivos macOS para o esprima e personalizar a janela de logon para mostrar ou ocultar botões de energia no Microsoft Intune. Consulte as etapas para obter o endereço IP, o caminho e as configurações de porta de um servidor de impressão em sua rede. Use essas configurações em um perfil de configuração de dispositivo para configurar recursos de dispositivo macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549930"
---
# <a name="macos-device-feature-settings-in-intune"></a>configurações de recurso de dispositivo macOS no Intune

O Intune inclui algumas configurações internas para personalizar recursos em seus dispositivos macOS. Este artigo lista essas configurações e descreve o que cada configuração faz. Ele também lista as etapas para obter o endereço IP, o caminho e a porta de impressoras de impressão ao usar o aplicativo de terminal (emulador).

Esta funcionalidade aplica-se a:

- macOS

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para criar uma faixa, escolha como os usuários entram, adicione um servidor de impressão e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de configuração de dispositivo MacOS](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **Endereço IP**: Insira o endereço IPv4 ou IPv6 da impressora. Se você usar nomes de host para identificar impressoras, poderá obter o endereço IP executando ping na impressora no aplicativo de terminal. [Obter o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Caminho**: Insira o caminho da impressora. O caminho é normalmente `ipp/print` para impressoras em sua rede. [Obter o endereço IP e o caminho](#get-the-ip-address-and-path) (neste artigo) fornece mais detalhes.
- **Porta** do (iOS 11,0 e posterior): Insira a porta de escuta do destino de impressão. Se você deixar essa propriedade em branco, o impresso usará a porta padrão.
- **TLS** (iOS 11,0 e posterior): Selecione **habilitar** para proteger conexões de esprint com segurança de camada de transporte (TLS).

**Adicionar** O servidor de impressão. Você pode adicionar muitos servidores de impressão.

- **Importar** (opcional): Você também pode **importar** um arquivo separado por vírgulas (. csv) que inclui uma lista de impressoras de impressão. Além disso, depois de adicionar impressoras de impressão no Intune, você pode **Exportar** essa lista.

Selecione **OK** para salvar suas configurações.

### <a name="get-the-ip-address-and-path"></a>Obter o endereço IP e o caminho

Para adicionar servidores do servidor de impressão, você precisa do endereço IP da impressora, do caminho do recurso e da porta. As etapas a seguir mostram como obter essas informações.

1. Em um Mac que está conectado à mesma rede local (sub-rede) que as impressoras de impressão impressa, abra o **terminal** (de **/Applications/Utilities**).
2. No aplicativo terminal, digite `ippfind`e selecione Enter.

    Anote as informações da impressora. Por exemplo, ele pode retornar algo semelhante a `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho do recurso.

3. No terminal, digite `ping myprinter.local`e selecione Enter.

   Anote o endereço IP. Por exemplo, ele pode retornar algo semelhante a `PING myprinter.local (10.50.25.21)`.

4. Use os valores de caminho de recurso e endereço IP. Neste exemplo, o endereço IP é `10.50.25.21`e o caminho do recurso é. `/ipp/port1`

## <a name="login-items"></a>Itens de logon

- **Arquivos, pastas e aplicativos personalizados**: **Adicione** o caminho de um arquivo, pasta, aplicativo personalizado ou aplicativo de sistema que você deseja abrir quando um usuário entrar no dispositivo. Aplicativos de sistema ou aplicativos criados ou personalizados para sua organização normalmente estão na `Applications` pasta, com um caminho semelhante a. `/Applications/AppName.app` 

  Você pode adicionar vários arquivos, pastas e aplicativos. Por exemplo, digite:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Ao adicionar qualquer aplicativo, pasta ou arquivo, certifique-se de inserir o caminho correto. Nem todos os itens estão na `Applications` pasta. Se um usuário mover um item de um local para outro, o caminho será alterado. Este item movido não será aberto quando o usuário entrar.

## <a name="login-window"></a>Janela de logon

### <a name="window-layout"></a>Layout da janela

- **Mostrar informações adicionais na barra de menus**: Quando a área de tempo na barra de menus é selecionada, **permitir** mostra o nome do host e a versão do MacOS. **Não configurado** (padrão) não mostra essas informações na barra de menus.
- **Faixa**: Insira uma mensagem que é mostrada na tela de entrada no dispositivo. Por exemplo, insira as informações da sua organização, uma mensagem de boas-vindas, informações perdidas e encontradas e assim por diante.
- **Escolher o formato de logon**: Escolha como os usuários entram no dispositivo. As opções são:
  - **Solicitar nome de usuário e senha** (padrão): Exige que os usuários insiram um nome de usuário e uma senha.
  - **Listar todos os usuários, solicitar senha**: Exige que os usuários selecionem seu nome de usuário em uma lista de usuários e, em seguida, insiram sua senha. Configure também:

    - **Usuários locais**: **Ocultar** não mostra as contas de usuário local na lista de usuários, que podem incluir as contas padrão e de administrador. Somente as contas de usuário de rede e de sistema são mostradas. **Não configurado** (padrão) mostra as contas de usuário local na lista de usuários.
    - **Contas móveis**: **Ocultar** não mostra contas móveis na lista de usuários. **Não configurado** (padrão) mostra as contas móveis na lista de usuários. Algumas contas móveis podem ser mostradas como usuários da rede.
    - **Usuários de rede**: Selecione **Mostrar** para listar os usuários de rede na lista de usuários. **Não configurado** (padrão) não mostra as contas de usuário de rede na lista de usuários.
    - **Usuários administradores**: **Ocultar** não mostra as contas de usuário administrador na lista de usuários. **Não configurado** (padrão) mostra as contas de usuário administrador na lista de usuários.
    - **Outros usuários**: Selecione **Mostrar** para listar **outros...** usuários na lista de usuários. **Não configurado** (padrão) não mostra as outras contas de usuário na lista de usuários.

### <a name="login-screen-power-settings"></a>Configurações de energia da tela de logon

- **Botão desligar**: **Ocultar** não mostra o botão de desligamento na tela de entrada. **Não configurado** (padrão) mostra o botão de desligamento.
- **Botão reiniciar**: **Ocultar** não mostra o botão reiniciar na tela de entrada. **Não configurado** (padrão) mostra o botão reiniciar.
- **Botão de suspensão**: **Ocultar** não mostra o botão de suspensão na tela de entrada. **Não configurado** (padrão) mostra o botão de suspensão.

### <a name="other"></a>Outros

- **Desabilitar logon de usuário do console do**: **Desabilitar** oculta a linha de comando MacOS usada para entrar. Para usuários típicos , desabilite essa configuração. **Não configurado** (padrão) permite que os usuários avançados entrem usando a linha de comando do macOS. Para entrar no modo de console, `>console` os usuários inserem no campo username e devem ser autenticados na janela do console.

### <a name="apple-menu"></a>Menu da Apple

Depois que os usuários entram nos dispositivos, as configurações a seguir afetam o que eles podem fazer.

- **Desabilitar**o desligamento: **Desabilitar** impede que os usuários selecionem a opção de desligamento após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu de desligamento no dispositivo.
- **Desabilitar**reinicialização: **Desabilitar** impede que os usuários selecionem a opção de reinicialização após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **reiniciar** no dispositivo.
- **Desabilitar**desligamento: **Desabilitar** impede que os usuários selecionem a opção desligar após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **desligar** no dispositivo.
- **Desabilitar logoff** (macOS 10,13 e posterior): **Desabilitar** impede que os usuários selecionem a opção **fazer logoff** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu **fazer logoff** no dispositivo.
- **Desabilitar tela de bloqueio** (macOS 10,13 e posterior): **Desabilitar** impede que os usuários selecionem a opção **tela de bloqueio** após o usuário entrar. **Não configurado** (padrão) permite que os usuários selecionem o item de menu da **tela de bloqueio** no dispositivo.

Selecione **OK** para salvar suas configurações.

## <a name="next-steps"></a>Passos seguintes

- Exiba todas as configurações para dispositivos [Ios](ios-device-features-settings.md) .
- [Atribua esse perfil](device-profile-assign.md) a seus grupos e [monitore seu status](device-profile-monitor.md).
