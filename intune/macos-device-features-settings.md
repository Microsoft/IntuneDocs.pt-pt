---
title: definições de funcionalidade do dispositivo macOS no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver todas as definições para configurar dispositivos macOS para AirPrint no Microsoft Intune. Consulte também os passos para obter o endereço IP, caminho e definições de porta de um servidor de AirPrint na sua rede. Utilize estas definições de um perfil de configuração do dispositivo para configurar dispositivos macOS para utilizar servidores de AirPrint na sua rede.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4973dc5038ecfe9a8e909df1a1db3feceb30979b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565337"
---
# <a name="macos-device-feature-settings-in-intune"></a>definições de funcionalidade do dispositivo macOS no Intune

O Intune inclui algumas definições incorporadas para permitir que o macOS os usuários imprimam em impressoras com o AirPrint na sua rede. Este artigo apresenta uma lista essas configurações e descreve o que faz cada definição. Ele também lista os passos para obter o endereço IP, caminho e impressoras de porta do AirPrint com a aplicação de Terminal (emulador).

## <a name="before-you-begin"></a>Antes de começar

[Criar perfil de configuração de dispositivo de um macOS](device-features-configure.md).

## <a name="airprint-settings"></a>Definições do AirPrint

1. Na **configurações**, selecione **AirPrint**. Introduza as seguintes propriedades do servidor AirPrint:

    - **Endereço IP**: Introduza o endereço IPv4 ou IPv6 da impressora. Se utilizar os nomes de anfitrião para identificar as impressoras, pode obter o endereço IP ao enviar pings para a impressora na aplicação do Terminal. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (Este artigo) fornece mais detalhes.
    - **Caminho**: Introduza o caminho da impressora. O caminho é normalmente `ipp/print` para impressoras na sua rede. [Obtenha o endereço IP e o caminho](#get-the-ip-address-and-path) (Este artigo) fornece mais detalhes.
    - **Porta**: Introduza a porta de escuta do destino AirPrint. Se deixar esta propriedade em branco, o AirPrint utiliza a porta predefinida. Disponível no iOS 11.0 e posterior.
    - **TLS**: Escolher **ativar** para proteger as ligações do AirPrint com Transport Layer Security (TLS). Disponível no iOS 11.0 e posterior.

2. Selecione **Adicionar**. O servidor do AirPrint é adicionado à lista. Pode adicionar vários servidores do AirPrint.

    Também pode **importação** um ficheiro separado por vírgulas (. csv) que inclui uma lista de impressoras com o AirPrint. Além disso, depois de adicionar impressoras com o AirPrint no Intune, pode **exportar** nesta lista.

3. Quando terminar, selecione **OK** para guardar a sua lista.

## <a name="get-the-ip-address-and-path"></a>Obtenha o endereço IP e o caminho

Para adicionar servidores AirPrinter, terá do endereço IP da impressora, o caminho de recurso e a porta. Os passos seguintes mostram como obter estas informações.

1. Num Mac que está ligado à mesma rede local (sub-rede) que as impressoras do AirPrint, abra **Terminal** (partir **/Applications/Utilities**).
2. Na aplicação do Terminal, escreva `ippfind`, e selecione introduzir.

    Tenha em atenção as informações de impressora. Por exemplo, pode retornar algo semelhante à `ipp://myprinter.local.:631/ipp/port1`. A primeira parte é o nome da impressora. A última parte (`ipp/port1`) é o caminho de recurso.

3. No Terminal, escreva `ping myprinter.local`, e selecione introduzir.

   Tenha em atenção o endereço IP. Por exemplo, pode retornar algo semelhante à `PING myprinter.local (10.50.25.21)`.

4. Utilize os valores de caminho de recursos e o endereço IP. Neste exemplo, é o endereço IP `10.50.25.21`, e o caminho de recurso é `/ipp/port1`.

## <a name="next-steps"></a>Passos Seguintes

- Ver todas as definições de [iOS](ios-device-features-settings.md) dispositivos.
- Atribua este perfil a grupos; ver [atribuir perfis de dispositivo](device-profile-assign.md).
