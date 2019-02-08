---
title: Definições de local público para o Windows e Holographic dispositivos no Microsoft Intune – Azure | Documentos da Microsoft
description: Configurar o Windows 10 (e posterior) e o Windows Holographic for Business dispositivos como quiosques de aplicação única e várias aplicações, personalizar o menu Iniciar, adicionar aplicações, mostrar a barra de tarefas e configurar um navegador da web no Microsoft Intune.
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
ms.openlocfilehash: c777beb294482a179d4b99fc71db031367698d0d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835797"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Windows 10 e Windows Holographic for Business, definições do dispositivo ser executado como um quiosque dedicado com o Intune

Em dispositivos Windows 10, utilize o Intune para executar dispositivos como um quiosque, por vezes conhecido como um dispositivo dedicado. Um dispositivo no modo de local público pode executar uma aplicação ou executar muitos aplicativos. Pode mostrar e personalizar um menu Iniciar, adicionar aplicações diferentes, incluindo aplicações de Win32, adicionar uma página home específica para um navegador da web e muito mais. 

Esta funcionalidade aplica-se a dispositivos que executam:

- Windows 10 e posterior
- Windows Holographic for Business

O Intune suporta um perfil de quiosque por dispositivo. Se precisar de vários perfis de quiosque num só dispositivo, poderá utilizar um [OMA-URI personalizado](custom-settings-windows-10.md).

O Intune utiliza "perfis de configuração" para criar e personalizar estas definições para as necessidades da sua organização. Depois de adicionar esses recursos num perfil, push ou implementar estas definições aos grupos na sua organização.

Este artigo mostra-lhe como criar um perfil de configuração do dispositivo. Para obter uma lista de todas as definições, e o que fazer, consulte [definições de local público do Windows 10](kiosk-settings-windows.md) e [Windows Holographic for Business, as definições de local público](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: Introduza um nome descritivo para o novo perfil.
   - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: Selecione **Windows 10 e posterior**
   - **Tipo de perfil**: Selecione **quiosque**

4. Na **configurações**, selecione um **modo de local público**. O **modo de quiosque** identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

    - **Não configurado** (predefinição): A política não ativar o modo de local público.
    - **Aplicação única, quiosque de ecrã inteiro**: O dispositivo é executado como uma conta de utilizador único e bloqueia-a numa única aplicação de Store. Quando o utilizador inicia sessão, é iniciada uma aplicação específica. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
    - **Quiosque de várias aplicações**: O dispositivo é executado Store de várias aplicações, as aplicações de Win32 ou aplicações de Windows de caixa de entrada usando o ID de modelo de utilizador de aplicação (AUMID). Apenas as aplicações que adicionar estarão disponíveis no dispositivo.

        A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, também não lhes permite ver as aplicações de que não precisam.

    Para obter uma lista de todas as definições e o que fazer, consulte:
      - [Definições de local público do Windows 10](kiosk-settings-windows.md)
      - [Windows Holographic for Business, as definições de local público](kiosk-settings-holographic.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações. 

O perfil é criado e apresentado na lista de perfis. Em seguida, [atribuir](device-profile-assign.md) o perfil.

## <a name="next-steps"></a>Passos Seguintes

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Pode criar perfis de local público para dispositivos que executam as seguintes plataformas:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings)
- [Windows 10 e posterior](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
