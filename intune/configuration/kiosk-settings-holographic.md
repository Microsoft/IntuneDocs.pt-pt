---
title: Configurações de quiosque para o Windows Holographic for Business no Microsoft Intune – Azure | Microsoft Docs
description: Configure seus dispositivos Windows Holographic para empresas como quiosques de aplicativo único e vários aplicativos, personalize o menu Iniciar, adicione aplicativos, mostre a barra de tarefas e configure um navegador da Web no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9318651dabcc93ef194c82b81b43fb25b98fb32
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730584"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Configurações do dispositivo Windows Holographic for Business para execução como um quiosque no Intune

Em dispositivos com o Windows Holographic for Business, pode configurar estes dispositivos para serem executados em modo de quiosque de uma aplicação ou modo de quiosque de várias aplicações. Algumas funcionalidades não são suportadas no Windows Holographic for Business.

Este artigo lista e descreve as diferentes configurações que você pode controlar em dispositivos Windows Holographic for Business. Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para configurar seus dispositivos Windows Holographic para empresas para serem executados no modo de quiosque.

Como administrador do Intune, você pode criar e atribuir essas configurações aos seus dispositivos.

Para saber mais sobre o recurso de quiosque do Windows no Intune, consulte [definir configurações de quiosque](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie o perfil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro

Ao escolher o modo de quiosque de uma aplicação, introduza as seguintes definições:

- **Tipo de logon do usuário**: Selecione **conta de usuário local** para inserir a conta de usuário local (para o dispositivo) ou uma conta da Microsoft (MSA) associada ao aplicativo de quiosque. Os tipos de conta de utilizador de **início de sessão automático** não são suportados pelo Windows Holographic for Business.

- **Tipo de aplicativo**: Selecione **aplicativo da loja**.

- **Aplicação a executar no modo de quiosque**: Escolha **Adicionar um aplicativo da loja**e selecione um aplicativo na lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](../apps/apps-add.md).

    Selecione **OK** para guardar as alterações.

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. Ao escolher o modo de quiosque de várias aplicações, introduza as seguintes definições:

- **Direcionar dispositivos Windows 10 em modo S**: Escolha **não**. Não há suporte para o modo S no Windows Holographic for Business.

- **Tipo de logon do usuário**: Adicione uma ou mais contas de usuário que podem usar os aplicativos que você adicionar. As opções são: 

  - **Logon automático**: Sem suporte no Windows Holographic for Business.
  - **Contas de usuário local**: **Adicione** a conta de usuário local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.
  - **Usuário ou grupo do Azure AD (Windows 10, versão 1803 e posterior)** : Requer credenciais de usuário para entrar no dispositivo. Selecione **Adicionar** para escolher os utilizadores ou grupos do Microsoft Azure AD na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta de visitante é uma conta de convidado que não requer nenhuma credencial de usuário ou autenticação, conforme descrito em [conceitos de modo de PC compartilhado](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicativos**: Adicione os aplicativos a serem executados no dispositivo de quiosque. Lembre-se de que pode adicionar várias aplicações.

  - **Adicionar aplicativos da Store**: Selecione um aplicativo existente que você adicionou ou implantou no Intune como [aplicativos cliente](../apps/apps-add.md), incluindo aplicativos LOB. Se você não tiver nenhum aplicativo listado, o Intune dá suporte a muitos [tipos de aplicativos](../apps/apps-add.md) que você [adiciona ao Intune](../apps/store-apps-windows.md).
  - **Adicionar aplicativo Win32**: Sem suporte no Windows Holographic for Business.
  - **Adicionar por AUMID**: Use esta opção para adicionar aplicativos do Windows de caixa de entrada. Introduza as seguintes propriedades: 

    - **Nome do aplicativo**: Necessário. Introduza um nome para a aplicação.
    - **ID do modelo de usuário do aplicativo (AUMID)** : Necessário. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Tamanho do bloco**: Necessário. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

- **Configurações do navegador de quiosque**: Sem suporte no Windows Holographic for Business.

- **Usar layout de início alternativo**: Escolha **Sim** para inserir um arquivo XML que descreve como os aplicativos são exibidos no menu Iniciar, incluindo a ordem dos aplicativos. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) dá algumas orientações e inclui um ficheiro XML específico para dispositivos com o Windows Holographic for Business.

- **Barra de tarefas do Windows**: Sem suporte no Windows Holographic for Business.

## <a name="next-steps"></a>Passos seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você também pode criar perfis de quiosque para dispositivos [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)e [Windows 10 e posteriores](kiosk-settings-windows.md) .
