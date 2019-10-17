---
title: Configurações de quiosque para dispositivos Windows e Holographic no Microsoft Intune – Azure | Microsoft Docs
description: Configure seus dispositivos Windows 10 (e posterior) e Windows Holographic para empresas como quiosques de aplicativo único e vários aplicativos, personalizar o menu Iniciar, adicionar aplicativos, mostrar a barra de tarefas e configurar um navegador da Web em Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 271b49a4c927bccb5cd967ea99b0d7bd5c2bd515
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492350"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Configurações do dispositivo Windows 10 e Windows Holographic para empresas para execução como um quiosque dedicado usando o Intune

Em dispositivos Windows 10, use o Intune para executar dispositivos como um quiosque, às vezes conhecido como um dispositivo dedicado. Um dispositivo no modo de quiosque pode executar um aplicativo ou executar muitos aplicativos. Você pode mostrar e personalizar um menu Iniciar, adicionar aplicativos diferentes, incluindo aplicativos Win32, adicionar um home page específico a um navegador da Web e muito mais. 

Este recurso se aplica a dispositivos que executam:

- Windows 10 e posterior
- Windows Holographic for Business

O Intune suporta um perfil de quiosque por dispositivo. Se precisar de vários perfis de quiosque num só dispositivo, poderá utilizar um [OMA-URI personalizado](custom-settings-windows-10.md).

O Intune usa "perfis de configuração" para criar e personalizar essas configurações para as necessidades da sua organização. Depois de adicionar esses recursos em um perfil, envie por Push ou implante essas configurações em grupos em sua organização.

Este artigo mostra como criar um perfil de configuração de dispositivo. Para obter uma lista de todas as configurações e o que elas fazem, consulte Configurações de [quiosque do Windows 10](kiosk-settings-windows.md) e [configurações de quiosque do Windows Holographic for Business](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.
3. Introduza as seguintes propriedades:

   - **Nome**: introduza um nome descritivo para o novo perfil.
   - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
   - **Plataforma**: selecione **Windows 10 e posterior**
   - **Tipo de perfil**: selecione **quiosque**

4. Em **configurações**, selecione um **modo de quiosque**. O **modo de quiosque** identifica o tipo de modo de quiosque suportado pela política. As opções incluem:

    - **Não configurado** (predefinição): a política não ativa o modo de quiosque.
    - **Quiosque de uma aplicação de ecrã inteiro**: o dispositivo é executado como uma única conta de utilizador e bloqueia-a para uma única aplicação da Loja. Quando o utilizador inicia sessão, é iniciada uma aplicação específica. Este modo também impede que o utilizador abra novas aplicações ou mude a aplicação em execução.
    - **Quiosque de várias aplicações**: o dispositivo executa várias aplicações da Loja, aplicações Win32 ou aplicações do Windows da caixa de entrada através do ID do Modelo de Utilizador da Aplicação (AUMID). Apenas as aplicações que adicionar estarão disponíveis no dispositivo.

        A vantagem de um quiosque de várias aplicações ou dispositivos de objetivo fixo é o facto de proporcionar uma experiência fácil de compreender pelos utilizadores através do acesso às aplicações de que precisam. Além disso, também não lhes permite ver as aplicações de que não precisam.

    Para obter uma lista de todas as configurações e o que elas fazem, consulte:
      - [Configurações de quiosque do Windows 10](kiosk-settings-windows.md)
      - [Configurações de quiosque do Windows Holographic para empresas](kiosk-settings-holographic.md)

5. Assim que terminar, selecione **OK** > **Criar** para guardar as alterações. 

O perfil é criado e mostrado na lista de perfis. Em seguida, [atribua](device-profile-assign.md) o perfil.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).

Você pode criar perfis de quiosque para dispositivos que executam as seguintes plataformas:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 e posterior](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
