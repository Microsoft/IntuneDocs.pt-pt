---
title: Adicionar ou definir configurações de educação no Microsoft Intune-Azure | Microsoft Docs
description: Use o aplicativo fazer um teste em um perfil de configuração de dispositivo em dispositivos Windows 10 e posteriores no Microsoft Intune. Crie um perfil de configuração usando as configurações de educação e insira uma URL de aplicativo de teste, escolha como os usuários entram, monitore a tela durante o teste e permita ou Evite sugestões de texto durante o teste.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a64c5c6779d3fcc34f4ff120ed27e7f300bc09b0
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/30/2019
ms.locfileid: "71301967"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Usar o aplicativo fazer um teste em dispositivos Windows 10 no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Perfis educacionais no Intune são projetados para que os alunos realizem um teste ou exame nos dispositivos. Esse recurso inclui o aplicativo **fazer um teste** e as configurações para adicionar uma URL de teste, escolher como os usuários finais entram no teste e muito mais. Este recurso dá suporte à seguinte plataforma:

- Windows 10 e posterior

Quando o usuário entra, o aplicativo fazer um teste é aberto automaticamente com o teste que você inseriu. Nenhum outro aplicativo pode ser executado no dispositivo enquanto o teste está em andamento. [Fazer testes no Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) fornece mais detalhes sobre o aplicativo fazer um teste.

Este artigo lista as etapas para criar um perfil de configuração de dispositivo no Microsoft Intune. Ele também inclui informações para ler e saber mais sobre as configurações de educação disponíveis para seus dispositivos Windows 10.

## <a name="create-a-device-profile"></a>Criar um perfil de dispositivo

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Escolha **Windows 10 e posterior**.
    - **Perfil**: Escolha o **perfil de educação**.

4. Insira as configurações que você deseja configurar:

    - [Windows 10 e posterior](education-settings-windows.md)

5. Selecione **OK** > **Criar** para guardar as alterações.

Após introduzir as suas definições e criar o perfil, este será apresentado na lista de perfis. Em seguida, [atribua este perfil a alguns grupos](device-profile-assign.md).

## <a name="next-steps"></a>Passos seguintes

Consulte uma lista das [configurações de educação do Windows 10](education-settings-windows.md) e suas descrições.

[Atribua o perfil](device-profile-assign.md) e [monitorize o respetivo estado](device-profile-monitor.md).
