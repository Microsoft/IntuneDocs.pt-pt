---
title: Definições de dispositivos do Windows Holographic Business – Microsoft Intune – Azure | Documentos da Microsoft
description: Saiba mais sobre como configurar definições de restrição de dispositivos no Microsoft Intune para Windows Holographic for Business, incluindo anular a inscrição, geolocalização, palavras-passe, instalar aplicações a partir da App Store, cookies e pop-ups no Microsoft Edge, Windows Defender, pesquisa, cloud e armazenamento, conectividade bluetooth, hora do sistema e dados de utilização no Azure.
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
ms.custom: seodec18
ms.openlocfilehash: 8479e69d661b163778a4d0b4eb1f68e729436f4e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831501"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows Holographic for Business definições do dispositivo para permitir ou restringir funcionalidades com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as diferentes definições que pode controlar o Windows Holographic for Business no dispositivos, como o Microsoft Hololens. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para permitir ou desativar funcionalidades, o controlo de segurança e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Anular inscrições manualmente**: Permite que o utilizador elimine manualmente a conta da área de trabalho do dispositivo.
- **Cortana**: Ativar ou desativar o assistente de voz Cortana.
- **Geolocalização**: Especifica se o dispositivo pode utilizar informações de serviços de localização.

## <a name="password"></a>Palavra-passe

- **palavra-passe**: Exija que o utilizador final introduza uma palavra-passe para aceder ao dispositivo.
- **Exigir palavra-passe quando o dispositivo regressa do Estado de inatividade**: Especifica que o utilizador tem de introduzir uma palavra-passe para desbloquear o dispositivo.

## <a name="app-store"></a>App Store

- **Atualização automática de aplicações da loja**: Permite que aplicações instaladas a partir da Microsoft Store sejam atualizadas automaticamente.
- **Instalação de aplicação fidedigna**: Permite que as aplicações assinadas com um certificado fidedigno sejam sideloaded.
- **Desbloqueio de programador**: Permitir que as definições de programador do Windows, como permitir que as aplicações de sideload sejam modificadas pelo utilizador final.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

- **Cookies**: Permite que o browser guarde cookies de internet no dispositivo.
- **Pop-ups**: Janelas de pop-up de blocos no browser (aplica-se apenas a computadores Windows 10).
- **Sugestões de pesquisa**: Permite que o motor de busca sugira sites à medida que escreve expressões de pesquisa.
- **Gestor de palavra-passe**: Ativar ou desativar a funcionalidade Gestor de palavra-passe do Microsoft Edge.
- **Enviar cabeçalhos de realizar rastreio não**: Configura o browser Microsoft Edge para enviar cabeçalhos do not track para sites que os utilizadores visitam.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para o Microsoft Edge**: Ative o Microsoft Edge SmartScreen para aceder ao site e transferências de ficheiros.

## <a name="search"></a>Pesquisa

- **Procurar localização** – especifica se a pesquisa pode utilizar informações de localização. informações

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Conta Microsoft**: Permite que o utilizador associe uma conta Microsoft ao dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Bluetooth**: Controla se o utilizador pode ativar e configurar o Bluetooth no dispositivo.
- **Deteção de Bluetooth**: Permite que o dispositivo seja detetado por outros dispositivos com Bluetooth ativado.
- **Publicidade do Bluetooth**: Permite que os dispositivos recebam anúncios por Bluetooth.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Modificação da hora do sistema**: Impede o utilizador final de alterar a data e hora.

## <a name="kiosk---obsolete"></a>Quiosque – Obsoleto

Estas definições são só de leitura e não podem ser alteradas. Para configurar o modo de quiosque, veja [Definições de quiosque](kiosk-settings-holographic.md).

Normalmente, um dispositivo de quiosque executa uma aplicação específica. Os utilizadores são impedidos de aceder a funcionalidades ou funções no dispositivo fora da aplicação de quiosque.

- **Modo de local público**: Identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

  - **Não configurado** (predefinição): A política não ativa o modo de local público. 
  - **Quiosque de uma aplicação**: O perfil ativa o dispositivo execute apenas uma aplicação. Quando um utilizador inicia sessão, uma aplicação específica é iniciada. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
  - **Quiosque de várias aplicações**: O perfil ativa o dispositivo execute múltiplas aplicações. Apenas as aplicações que adicionar estão disponíveis para o utilizador. A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, permite que os utilizadores ocultem as aplicações de que não precisam. 
  
    Ao adicionar aplicações a uma experiência de quiosque de várias aplicações, também adiciona um ficheiro de esquema do menu Iniciar. O [ficheiro de esquema do menu Iniciar](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) inclui um XML de exemplo que pode ser utilizado no Intune. 

#### <a name="single-app-kiosks"></a>Quiosques de uma aplicação

Introduza as seguintes definições:

- **Conta de utilizador**: Introduza a conta de utilizador local (para o dispositivo) ou a conta do Azure AD associado à aplicação de local público de início de sessão. Para contas associadas a domínios do Azure AD, introduza a conta com o formato `domain\username@tenant.org`. 

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `AzureAD\user@contoso.com`.

- **O modelo de utilizador de aplicação ID (AUMID) da aplicação**: Introduza o AUMID da aplicação de local público. Para saber mais, veja [Find the Application User Model ID of an installed app (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Relatórios e Telemetria

- **Partilhar dados de utilização**: Selecione o nível de submissão de dados de diagnóstico.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
