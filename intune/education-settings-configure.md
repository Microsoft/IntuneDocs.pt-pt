---
title: Adicione ou configure as definições de educação no Microsoft Intune – Azure | Documentos da Microsoft
description: Utilize o aplicação fazer um teste num perfil de configuração do dispositivo no Windows 10 e dispositivos posteriores no Microsoft Intune. Criar um perfil de configuração usando settiings educação e introduza um URL de aplicação de teste, escolha como os utilizadores início de sessão, monitorizar a tela durante o teste e permitirem ou impedem a sugestões de texto durante o teste.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efa990e12416c292d9446428165e4bff99c7eca2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57393210"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Utilizar o aplicação fazer um teste em dispositivos Windows 10 no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os perfis de educação no Intune foram concebidos para os estudantes realizarem um teste ou o exame nos dispositivos. Esta funcionalidade inclui a **fazer um teste** aplicações e definições para adicionar um URL de teste, escolha como os utilizadores finais iniciar sessão para o teste e muito mais. Esta funcionalidade suporta a plataforma seguinte:

- Windows 10 e posterior

Quando o utilizador inicia sessão, o aplicação fazer um teste abre-se automaticamente com o teste que introduziu. Nenhuma outra aplicação pode executar no dispositivo, enquanto o teste está em curso. [Realizar testes no Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) fornece mais detalhes sobre como fazer uma aplicação de teste.

Este artigo lista os passos para criar um perfil de configuração do dispositivo no Microsoft Intune. Também inclui informações para ler e saber mais sobre as definições de educação disponíveis para os seus dispositivos Windows 10.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolher **Windows 10 e posterior**.
    - **Perfil**: Escolher **perfil de educação**.

4. Introduza as definições que pretende configurar:

    - [Windows 10 e posterior](education-settings-windows.md)

5. Selecione **OK** > **Criar** para guardar as alterações.

Após introduzir as suas definições e criar o perfil, este será apresentado na lista de perfis. Em seguida, [atribua este perfil a alguns grupos](device-profile-assign.md).

## <a name="next-steps"></a>Passos Seguintes

Ver uma lista do [as definições de educação do Windows 10](education-settings-windows.md) e suas descrições.

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
