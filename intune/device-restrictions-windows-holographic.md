---
title: Restrições de dispositivos para o Windows Holographic for Business no Microsoft Intune – Azure | Microsoft Docs
description: Saiba mais sobre como configurar definições de restrição de dispositivos no Microsoft Intune para Windows Holographic for Business, incluindo anular a inscrição, geolocalização, palavras-passe, instalar aplicações a partir da App Store, cookies e pop-ups no Microsoft Edge, Windows Defender, pesquisa, cloud e armazenamento, conectividade bluetooth, hora do sistema e dados de utilização no Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5f201544ec92ec57ec537a904075237020be168c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182623"
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Definições de restrição de dispositivos para o Windows Holographic for Business no Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

As seguintes definições de restrição de dispositivos são suportadas em dispositivos com o Windows Holographic for Business, tais como o Microsoft Hololens.

## <a name="general"></a>Geral

- **Anular inscrições manualmente** – Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
- **Cortana** – Ative ou desative o assistente de voz Cortana.
- **Geolocalização** – Especifica se o dispositivo pode utilizar informações de serviços de localização.

## <a name="password"></a>Palavra-passe
-   **Palavra-passe** – exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
    -   **Exigir palavra-passe quando o dispositivo regressa do estado de inatividade** – especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo.

## <a name="app-store"></a>App Store

-   **Atualização automática de aplicações a partir da loja** – permite que as aplicações instaladas a partir da Loja Microsoft sejam atualizadas automaticamente.
-   **Instalação de aplicação fidedigna** – permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
-   **Desbloqueio de programador** – permita as definições de programador do Windows, tais como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

-   **Cookies** – Permite que o browser guarde cookies de Internet no dispositivo.
-   **Pop-ups** – bloqueia as janelas pop-up no browser (aplica-se apenas ao ambiente de trabalho do Windows 10).
-   **Sugestões de pesquisa** – Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
-   **Gestor de Palavras-Passe** – ativa ou desativa a funcionalidade Gestor de Palavras-Passe do Microsoft Edge.
- **Enviar cabeçalhos Do Not Track** – configura o browser Microsoft Edge para enviar cabeçalhos Do Not Track para sites que os utilizadores visitam.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para o Microsoft Edge** – ativa o Microsoft Edge SmartScreen para aceder ao site e às transferências de ficheiros.

## <a name="search"></a>Procura
- **Procurar localização** – especifica se a pesquisa pode utilizar informações de localização. informações

## <a name="cloud-and-storage"></a>Cloud e Armazenamento
-   **Conta Microsoft** – Permite que o utilizador associe uma conta Microsoft ao dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

-   **Bluetooth** – Controla se o utilizador pode ativar e configurar Bluetooth do dispositivo.
-   **Deteção de Bluetooth** – Permite que este dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
-   **Publicidade do Bluetooth** – Permite que o dispositivo receba anúncios através de Bluetooth.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Modificação da Hora do Sistema** –impede o utilizador final de alterar a data e a hora do dispositivo.

## <a name="kiosk---obsolete"></a>Quiosque – Obsoleto

Estas definições são só de leitura e não podem ser alteradas. Para configurar o modo de quiosque, veja [Definições de quiosque](kiosk-settings.md#windows-holographic-for-business).

Normalmente, um dispositivo de quiosque executa uma aplicação específica. Os utilizadores são impedidos de aceder a funcionalidades ou funções no dispositivo fora da aplicação de quiosque.

- **Modo de quiosque** – identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

  - **Não Configurado** (predefinição) – a política não ativa um modo de local público. 
  - **Quiosque de uma aplicação** – o perfil permite que o dispositivo execute apenas uma aplicação. Quando um utilizador inicia sessão, uma aplicação específica é iniciada. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
  - **Quiosque de várias aplicações** – o perfil permite que o dispositivo execute múltiplas aplicações. Apenas as aplicações que adicionar estão disponíveis para o utilizador. A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, permite que os utilizadores ocultem as aplicações de que não precisam. 
  
    Ao adicionar aplicações a uma experiência de quiosque de várias aplicações, também adiciona um ficheiro de esquema do menu Iniciar. O [ficheiro de esquema do menu Iniciar](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) inclui um XML de exemplo que pode ser utilizado no Intune. 

#### <a name="single-app-kiosks"></a>Quiosques de uma aplicação
Introduza as seguintes definições:

- **Conta de utilizador** – introduza a conta de utilizador local (no dispositivo) ou o início de sessão de conta do Azure AD associado à aplicação de quiosque. Para contas associadas a domínios do Azure AD, introduza a conta com o formato `domain\username@tenant.org`. 

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `AzureAD\user@contoso.com`.

- **ID do modelo do utilizador da aplicação (AUMID) da aplicação** – introduza o AUMID da aplicação do quiosque. Para saber mais, veja [Find the Application User Model ID of an installed app (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Relatórios e Telemetria

- **Partilhar dados de utilização** – selecione o nível da submissão dos dados de diagnóstico.
