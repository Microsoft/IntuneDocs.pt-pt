---
title: "Definições de restrição de dispositivos no Intune para dispositivos Windows Holographic for Business"
titlesuffix: Azure portal
description: "Saiba quais são as definições do Intune que pode utilizar para controlar as definições dos dispositivos e a funcionalidade em dispositivos Windows Holographic for Business."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/19/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 300ddb15f2d7b8f2fc6ab4a0e9e32852e0604e0a
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/01/2018
---
# <a name="windows-holographic-for-business-device-restriction-settings-in-microsoft-intune"></a>Definições de restrição de dispositivos no Microsoft Intune para dispositivos Windows Holographic for Business

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As seguintes definições de restrição de dispositivos são suportadas em dispositivos com o Windows Holographic for Business, tais como o Microsoft Hololens.

## <a name="general"></a>Geral

- **Anular inscrições manualmente** – permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
- **Cortana** – ative ou desative o assistente de voz Cortana.
- **Geolocalização** – especifica se o dispositivo pode utilizar informações de serviços de localização.



## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade** – especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo.



## <a name="app-store"></a>Loja de Aplicações

-   **Loja de aplicações** – ative ou bloqueie a utilização da loja de aplicações em dispositivos.
-   **Atualização automática de aplicações a partir da loja** – permite que as aplicações instaladas a partir da Loja Microsoft sejam atualizadas automaticamente.
-   **Instalação de aplicação fidedigna** – permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
-   **Desbloqueio de programador** – permita as definições de programador do Windows, tais como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.

## <a name="edge-browser"></a>Browser Edge

-   **Browser Microsoft Edge** – permita a utilização do browser Edge no dispositivo.
-   **Cookies** – permite que o browser guarde cookies de Internet no dispositivo.
-   **Pop-ups** – bloqueia as janelas pop-up no browser (aplica-se apenas ao ambiente de trabalho do Windows 10).
-   **Sugestões de pesquisa** – permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
-   **Gestor de Palavras-passe** – ative ou desative a funcionalidade Gestor de Palavras-passe do Microsoft Edge.
- **Enviar cabeçalhos Do Not Track** – configura o browser Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para Microsoft Edge** – ative o Edge SmartScreen para aceder ao site e às transferências de ficheiros.

## <a name="search"></a>Procura
- **Procurar localização** – especifica se a pesquisa pode utilizar informações de localização. informações


## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-   **Conta Microsoft** – permite que o utilizador associe uma conta Microsoft ao dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

-   **Bluetooth** – controla se o utilizador pode ativar e configurar Bluetooth do dispositivo.
-   **Deteção de Bluetooth** – permite que este dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
-   **Publicidade do Bluetooth** – permite que o dispositivo receba anúncios através de Bluetooth.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Modificação da Hora do Sistema** – impede o utilizador final de alterar a data e a hora do dispositivo.

## <a name="reporting-and-telemetry"></a>Relatórios e Telemetria

- **Partilhar dados de utilização** – selecione o nível da submissão dos dados de diagnóstico.