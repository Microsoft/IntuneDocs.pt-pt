---
title: definições de funcionalidade do dispositivo macOS no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver as definições para configurar dispositivos macOS para AirPrint e personalizar a janela de início de sessão para mostrar ou ocultar botões de energia no Microsoft Intune. Veja os passos para obter o endereço IP, caminho e definições de porta de um servidor de AirPrint na sua rede. Utilize estas definições de um perfil de configuração do dispositivo para configurar funcionalidades de dispositivos macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1826498b3bfa2191900d7574f79051af8f758558
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041705"
---
# <a name="macos-device-feature-settings-in-intune"></a>definições de funcionalidade do dispositivo macOS no Intune

O Intune inclui algumas definições incorporadas para personalizar funcionalidades nos seus dispositivos macOS. Este artigo apresenta uma lista essas configurações e descreve o que faz cada definição. Ele também lista os passos para obter o endereço IP, caminho e impressoras de porta do AirPrint com a aplicação de Terminal (emulador).

Esta funcionalidade aplica-se a:

- macOS

Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para criar uma faixa, escolha a forma como os utilizadores iniciam sessão, adicionar um servidor do AirPrint e muito mais.

Estas definições são adicionadas a um perfil de configuração do dispositivo no Intune e, em seguida, atribuídas ou implementadas nos dispositivos macOS.

## <a name="before-you-begin"></a>Antes de começar

[Criar perfil de configuração de dispositivo de um macOS](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **Endereço IP**: Introduza o endereço IPv4 ou IPv6 da impressora. Se usar nomes de anfitrião para identificar as impressoras, pode obter o endereço IP ao enviar pings para a impressora na aplicação do Terminal. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (Este artigo) fornece mais detalhes.
- **Caminho**: Introduza o caminho da impressora. O caminho é normalmente `ipp/print` para impressoras na sua rede. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (Este artigo) fornece mais detalhes.
- **Porta** (iOS 11.0 e posterior): Introduza a porta de escuta do destino AirPrint. Se deixar esta propriedade em branco, o AirPrint utiliza a porta predefinida.
- **TLS** (iOS 11.0 e posterior): Selecione **ativar** para proteger as ligações do AirPrint com Transport Layer Security (TLS).

**Adicionar** AirPrint o servidor. Pode adicionar vários servidores do AirPrint.

- **Importar** (opcional): Também pode **importação** um ficheiro separado por vírgulas (. csv) que inclui uma lista de impressoras com o AirPrint. Além disso, depois de adicionar impressoras com o AirPrint no Intune, pode **exportar** nesta lista.

Selecione **OK** para guardar as definições.

### <a name="get-the-ip-address-and-path"></a>Obtenha o endereço IP e o caminho

Para adicionar servidores AirPrinter, terá do endereço IP da impressora, o caminho de recurso e a porta. Os passos seguintes mostram como obter estas informações.

1. Num Mac que está ligado à mesma rede local (sub-rede) que as impressoras do AirPrint, abra **Terminal** (partir **/Applications/Utilities**).
2. Na aplicação do Terminal, escreva `ippfind`, e selecione introduzir.

    Tenha em atenção as informações de impressora. Por exemplo, pode retornar algo semelhante à `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho de recurso.

3. No Terminal, escreva `ping myprinter.local`, e selecione introduzir.

   Tenha em atenção o endereço IP. Por exemplo, pode retornar algo semelhante à `PING myprinter.local (10.50.25.21)`.

4. Utilize os valores de caminho de recursos e o endereço IP. Neste exemplo, é o endereço IP `10.50.25.21`, e o caminho de recurso é `/ipp/port1`.

## <a name="login-window"></a>Janela de início de sessão

### <a name="window-layout"></a>Layout de janela

- **Mostrar informações adicionais na barra de menus**: Quando a área de tempo na barra de menu é selecionada, **permitir** mostra o anfitrião de versão de nome e macOS. **Não configurado** (predefinição) não mostra estas informações na barra de menus.
- **Faixa**: Introduza uma mensagem que é apresentada no ecrã do dispositivo de início de sessão. Por exemplo, introduza as informações da organização, uma mensagem de boas-vindas, informações de perdida e encontrado e assim por diante.
- **Escolha o formato de início de sessão**: Escolha como os utilizadores iniciam sessão no dispositivo. As opções são:
  - **Pedido de nome de utilizador e palavra-passe** (predefinição): Requer que os utilizadores introduzam um nome de utilizador e palavra-passe.
  - **Listar todos os utilizadores, pedidos de palavra-passe**: Requer que os utilizadores selecionar o respetivo nome de utilizador de uma lista de utilizador e, em seguida, introduza a palavra-passe. Também configure:

    - **Os usuários locais**: **Ocultar** não mostra as contas de utilizador local na lista de utilizadores, que pode incluir as contas standard e administrador. São apresentadas apenas as contas de utilizador de rede e sistema. **Não configurado** (predefinição) apresenta as contas de utilizador local, na lista de utilizadores.
    - **Contas móveis**: **Ocultar** não mostra contas móveis na lista de utilizadores. **Não configurado** (predefinição) mostra as contas de móveis na lista de utilizadores. Algumas contas móveis podem mostrar como os utilizadores da rede.
    - **Os utilizadores de rede**: Selecione **mostrar** para listar os utilizadores de rede na lista de utilizadores. **Não configurado** (predefinição) não mostra a rede de contas de utilizador na lista de utilizadores.
    - **Os utilizadores administradores**: **Ocultar** não mostra contas de utilizador o administrador na lista de utilizadores. **Não configurado** (predefinição) mostra o administrador de contas de utilizador na lista de utilizadores.
    - **Outros usuários**: Selecione **mostrar** à lista **outros...**  os utilizadores da lista de utilizador. **Não configurado** (predefinição) não mostra as contas de utilizador na lista de utilizadores.

### <a name="login-screen-power-settings"></a>Definições de energia do ecrã de início de sessão

- **Botão Encerrar**: **Ocultar** não mostra o botão Encerrar no ecrã de início de sessão. **Não configurado** (predefinição) mostra o botão de encerramento.
- **Reinicie o botão**: **Ocultar** não mostra o botão de reinício no ecrã de início de sessão. **Não configurado** (predefinição) mostra o botão de reinício.
- **Botão de suspensão**: **Ocultar** não mostra o botão de suspensão no ecrã de início de sessão. **Não configurado** (predefinição) mostra o botão de suspensão.

### <a name="other"></a>Outros

- **Desativar início de sessão do utilizador da consola**: **Desativar** oculta a linha de comandos do macOS utilizada para iniciar sessão. Para os usuários comuns, **desativar** esta definição. **Não configurado** (predefinição) permite que os utilizadores avançados que inicie sessão com a linha de comandos do macOS. Para entrar no modo de consola, os utilizadores introduzirem `>console` o nome de utilizador de campo e tem de ser autenticado na janela da consola.

### <a name="apple-menu"></a>Apple Menu

Depois dos utilizadores iniciam sessão para os dispositivos, as seguintes definições de impacto sobre o que podem fazer.

- **Desativar desligar baixo**: **Desativar** impede que os utilizadores de selecionar as **encerramento** opção depois do utilizador inicia sessão. **Não configurado** (predefinição) permite que os utilizadores selecionem o **encerramento** item de menu no dispositivo.
- **Desativar reinício**: **Desativar** impede que os utilizadores de selecionar as **reiniciar** opção depois do utilizador inicia sessão. **Não configurado** (predefinição) permite que os utilizadores selecionem o **reiniciar** item de menu no dispositivo.
- **Desativar Power desativar**: **Desativar** impede que os utilizadores de selecionar as **desligar** opção depois do utilizador inicia sessão. **Não configurado** (predefinição) permite que os utilizadores selecionem o **desligar** item de menu no dispositivo.
- **Desativar terminar sessão** (macOS 10.13 e posterior): **Desativar** impede que os utilizadores de selecionar as **terminar sessão** opção depois do utilizador inicia sessão. **Não configurado** (predefinição) permite que os utilizadores selecionem o **terminar sessão** item de menu no dispositivo.
- **Desativar o ecrã de bloqueio** (macOS 10.13 e posterior): **Desativar** impede que os utilizadores de selecionar as **ecrã de bloqueio** opção depois do utilizador inicia sessão. **Não configurado** (predefinição) permite que os utilizadores selecionem o **ecrã de bloqueio** item de menu no dispositivo.

Selecione **OK** para guardar as definições.

## <a name="next-steps"></a>Passos Seguintes

- Ver todas as definições de [iOS](ios-device-features-settings.md) dispositivos.
- [Atribuir este perfil](device-profile-assign.md) aos seus grupos, e [monitorizar o estado](device-profile-monitor.md).
