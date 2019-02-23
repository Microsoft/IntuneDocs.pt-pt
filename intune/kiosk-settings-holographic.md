---
title: Definições de local público para o Windows Holographic for Business no Microsoft Intune – Azure | Documentos da Microsoft
description: Configurar o Windows Holographic for Business dispositivos como quiosques de aplicação única e várias aplicações, personalizar o menu Iniciar, adicionar aplicações, mostrar a barra de tarefas e configurar um navegador da web no Microsoft Intune.
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
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c5fd9998a4816775b3fc1d7803dc26e223b1e39
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742444"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Windows Holographic for Business, definições do dispositivo ser executado como um quiosque no Intune

Em dispositivos com o Windows Holographic for Business, pode configurar estes dispositivos para serem executados em modo de quiosque de uma aplicação ou modo de quiosque de várias aplicações. Algumas funcionalidades não são suportadas no Windows Holographic for Business.

Este artigo apresenta e descreve as diferentes definições que pode controlar o Windows Holographic for Business no dispositivos. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para configurar o Windows Holographic for Business dispositivos sejam executadas em modo de local público.

Enquanto administrador do Intune, pode criar e atribuir estas definições para os seus dispositivos.

Para saber mais sobre a funcionalidade de quiosque do Windows no Intune, veja [configurar definições de local público](kiosk-settings.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar o perfil](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Quiosques de uma aplicação em ecrã inteiro

Ao escolher o modo de quiosque de uma aplicação, introduza as seguintes definições:

- **Tipo de início de sessão do utilizador**: Selecione **conta de utilizador Local** para introduzir a conta de utilizador local (para o dispositivo) ou uma conta de conta Microsoft (MSA) associado à aplicação de local público. Os tipos de conta de utilizador de **início de sessão automático** não são suportados pelo Windows Holographic for Business.

- **Tipo de aplicação**: Selecione **Store app**.

- **Aplicação seja executada no modo de quiosque**: Escolher **adicionar uma aplicação da loja**e selecione uma aplicação a partir da lista.

    Não tem aplicações listadas? Adicione algumas através dos passos indicados em [Aplicações de Cliente](apps-add.md).

    Selecione **OK** para guardar as alterações.

## <a name="multi-app-kiosks"></a>Quiosques de várias aplicações

As aplicações neste modo estão disponíveis no menu Iniciar. Estas aplicações são as únicas aplicações que o utilizador pode abrir. Ao escolher o modo de quiosque de várias aplicações, introduza as seguintes definições:

- **O destino do Windows 10 no dispositivos de modo S**: Escolher **não**. Modo de S não é suportado no Windows Holographic for Business.

- **Tipo de início de sessão do utilizador**: Adicione um ou mais contas de utilizador que podem utilizar as aplicações que adicionar. As opções são: 

  - **Início de sessão automático**: Não é suportada no Windows Holographic for Business.
  - **Contas de utilizador local**: **Adicionar** a conta de utilizador local (para o dispositivo). A conta que introduzir serve para iniciar sessão no quiosque.
  - **Utilizador do Azure AD ou de grupo (Windows 10, versão 1803 e posterior)**: Requer credenciais de utilizador para iniciar sessão no dispositivo. Selecione **Adicionar** para escolher os utilizadores ou grupos do Microsoft Azure AD na lista. Pode selecionar vários utilizadores e grupos. Escolha **Selecionar** para guardar as alterações.
  - **Visitante do HoloLens**: A conta do visitante é uma conta de convidado que não requer credenciais de utilizador ou a autenticação, conforme descrito em [partilhados conceitos de modo de PC](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Aplicativos**: Adicione as aplicações para executar no dispositivo local público. Lembre-se de que pode adicionar várias aplicações.

  - **Adicionar aplicações de Store**: Selecione uma aplicação existente que foi adicionado com [aplicações de cliente](apps-add.md). Se não tiver aplicações listadas, poderá obter aplicações e [adicioná-las ao Intune](store-apps-windows.md).
  - **Adicionar aplicação Win32**: Não é suportada no Windows Holographic for Business.
  - **Adicionar por AUMID**: Utilize esta opção para adicionar aplicações de Windows de caixa de entrada. Introduza as seguintes propriedades: 

    - **Nome da aplicação**: Necessário. Introduza um nome para a aplicação.
    - **O modelo de utilizador de aplicação ID (AUMID)**: Necessário. Introduza o ID do modelo de utilizador da aplicação (AUMID) da aplicação Windows. Para obter este ID, veja [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Localizar o ID do Modelo de Utilizador da Aplicação de uma aplicação instalada).
    - **Mosaico tamanho**: Necessário. Escolha um tamanho de mosaico da aplicação: Pequeno, Médio, Largo ou Grande.

- **Definições do browser de local público**: Não é suportada no Windows Holographic for Business.

- **Esquema de iniciar alternativa utilize**: Escolher **Sim** para introduzir um arquivo XML que descreve a forma como as aplicações são apresentadas no menu Iniciar, incluindo a ordem das aplicações. Utilize esta opção se precisar de uma personalização adicional no menu Iniciar. O artigo [Customize and export start layout (Personalizar e exportar o esquema do menu Iniciar)](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) dá algumas orientações e inclui um ficheiro XML específico para dispositivos com o Windows Holographic for Business.

- **Barra de tarefas do Windows**: Não é suportada no Windows Holographic for Business.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Também pode criar perfis de local público para [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings), e [Windows 10 e posterior](kiosk-settings-windows.md) dispositivos.
