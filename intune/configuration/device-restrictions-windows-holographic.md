---
title: Configurações de dispositivo de negócios do Windows Holographic-Microsoft Intune-Azure | Microsoft Docs
description: Saiba mais sobre como configurar definições de restrição de dispositivos no Microsoft Intune para Windows Holographic for Business, incluindo anular a inscrição, geolocalização, palavras-passe, instalar aplicações a partir da App Store, cookies e pop-ups no Microsoft Edge, Windows Defender, pesquisa, cloud e armazenamento, conectividade bluetooth, hora do sistema e dados de utilização no Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e28a697b841d8b264a19d97059d272b7119bc7f4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493915"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Configurações do dispositivo Windows Holographic for Business para permitir ou restringir recursos usando o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo lista e descreve as diferentes configurações que você pode controlar em dispositivos Windows Holographic for Business, como o Microsoft Hololens. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para permitir ou desabilitar recursos, segurança de controle e muito mais.

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Geral

- **Cancelamento de registro manual**: permite que o usuário exclua manualmente a conta do local de trabalho do dispositivo.
- **Cortana**: habilitar ou desabilitar o assistente de voz Cortana.
- **Geolocalização**: especifica se o dispositivo pode usar informações de serviços de localização.

## <a name="password"></a>Palavra-passe

- **Senha**: exige que o usuário final Insira uma senha para acessar o dispositivo.
- **Exigir senha quando o dispositivo retorna do estado ocioso**: Especifica que o usuário deve inserir uma senha para desbloquear o dispositivo.

## <a name="app-store"></a>App Store

- **Atualizar aplicativos automaticamente da loja**: permite que os aplicativos instalados no Microsoft Store sejam atualizados automaticamente.
- **Instalação de aplicativo confiável**: permite que aplicativos assinados com um certificado confiável sejam Sideload.
- **Desbloqueio do desenvolvedor**: permitir configurações do desenvolvedor do Windows, como permitir que aplicativos Sideload sejam modificados pelo usuário final.

## <a name="microsoft-edge-browser"></a>Browser Microsoft Edge

- **Cookies**: permite que o navegador salve cookies da Internet no dispositivo.
- **Pop-ups**: bloqueia janelas pop-up no navegador (aplica-se somente ao Windows 10 Desktop).
- **Sugestões de pesquisa**: permite que o mecanismo de pesquisa sugira sites à medida que você digita frases de pesquisa.
- **Gerenciador de senhas**: habilitar ou desabilitar o recurso Gerenciador de senhas do Microsoft Edge.
- **Enviar cabeçalhos do not Track**: configura o navegador Microsoft Edge para enviar cabeçalhos não rastrear aos sites visitados pelos usuários.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen para Microsoft Edge**: habilitar o SmartScreen do Microsoft Edge para acessar downloads de site e arquivo.

## <a name="search"></a>Procura

- **Procurar localização** – especifica se a pesquisa pode utilizar informações de localização. informações

## <a name="cloud-and-storage"></a>Cloud e Armazenamento

- **Conta Microsoft**: permite que o usuário associe um conta Microsoft ao dispositivo.

## <a name="cellular-and-connectivity"></a>Rede Móvel e Conectividade

- **Bluetooth**: controla se o usuário pode habilitar e configurar o Bluetooth no dispositivo.
- **Descoberta de Bluetooth**: permite que o dispositivo seja descoberto por outros dispositivos habilitados para Bluetooth.
- **Publicidade de Bluetooth**: permite que o dispositivo receba anúncios via Bluetooth.

## <a name="control-panel-and-settings"></a>Painel de Controlo e Definições

- **Modificação de horário do sistema**: impede que o usuário final altere a data e a hora do dispositivo.

## <a name="kiosk---obsolete"></a>Quiosque – Obsoleto

Estas definições são só de leitura e não podem ser alteradas. Para configurar o modo de quiosque, veja [Definições de quiosque](kiosk-settings-holographic.md).

Normalmente, um dispositivo de quiosque executa uma aplicação específica. Os utilizadores são impedidos de aceder a funcionalidades ou funções no dispositivo fora da aplicação de quiosque.

- **Modo de quiosque**: identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

  - **Não configurado** (predefinição): a política não ativa um modo de quiosque. 
  - **Quiosque de aplicativo único**: o perfil permite que o dispositivo execute apenas um aplicativo. Quando um utilizador inicia sessão, uma aplicação específica é iniciada. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
  - **Quiosque de vários aplicativos**: o perfil permite que o dispositivo execute vários aplicativos. Apenas as aplicações que adicionar estão disponíveis para o utilizador. A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, permite que os utilizadores ocultem as aplicações de que não precisam. 
  
    Ao adicionar aplicações a uma experiência de quiosque de várias aplicações, também adiciona um ficheiro de esquema do menu Iniciar. O [ficheiro de esquema do menu Iniciar](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) inclui um XML de exemplo que pode ser utilizado no Intune. 

### <a name="single-app-kiosks"></a>Quiosques de uma aplicação

Introduza as seguintes definições:

- **Conta de usuário**: Insira a conta de usuário local (para o dispositivo) ou o logon de conta do Azure ad associado ao aplicativo de quiosque. Para contas associadas a domínios do Azure AD, introduza a conta com o formato `domain\username@tenant.org`. 

    Para ambientes de quiosque com início de sessão automático ativado, deve ser utilizado um tipo de utilizador com o menor privilégio (tal como a conta de utilizador padrão local). Para configurar uma conta do Azure Active Directory (AD) para o modo de quiosque, utilize o formato `AzureAD\user@contoso.com`.

- **ID do modelo de usuário do aplicativo (AUMID) do**aplicativo: Insira o AUMID do aplicativo de quiosque. Para saber mais, veja [Find the Application User Model ID of an installed app (Localizar o ID de Modelo do Utilizador da Aplicação de uma aplicação instalada)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Relatórios e Telemetria

- **Compartilhar dados de uso**: selecione o nível de envio de dados de diagnóstico.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
