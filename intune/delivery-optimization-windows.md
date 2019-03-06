---
title: As definições de otimização de entrega para o Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Configure como os dispositivos Windows 10 que gere com o Intune utilizam Otimização da entrega. No Intune, crie um perfil de configuração do dispositivo para instalar atualizações a partir da internet. Veja também como substituir cadências de atualização existente com um perfil de otimização de entrega.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 3c10843e0ba0250da6bfce64fbc87b8ecbde7bb1
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57399060"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Definições de otimização de entrega no Microsoft Intune

Com o Intune, pode utilizar definições de otimização de entrega dos seus dispositivos Windows 10 para reduzir o consumo de largura de banda quando esses dispositivos transferir aplicações e atualizações. Otimização da entrega está configurada como parte de seus perfis de configuração do dispositivo.  

Este artigo descreve como configurar as definições de otimização de entrega como parte de um perfil de configuração do dispositivo. Depois de criar um perfil, em seguida, atribua ou implementar esse perfil para os seus dispositivos Windows 10. 

Para obter uma lista das definições de otimização de entrega que o Intune suporta, consulte [definições de otimização de entrega para o Intune](delivery-optimization-settings.md).  

Para saber mais sobre a otimização de entrega no Windows 10, veja [otimização de entrega de atualizações](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) na documentação do Windows.  


> [!NOTE]
> **Atualizações de software-Cadências de atualização do Windows 10** são substituídos pela **Otimização da entrega** definições. Os anéis de atualização existente podem ser alterados para utilizar o **Otimização da entrega** definições. [Mover cadências de atualização existente para otimização de entrega](#move-existing-update-rings-to-delivery-optimization) (neste artigo) 
## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.

2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.

3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione a plataforma:  

        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **Otimização da entrega**.
    - **Definições**: Configure as definições que definem como pretende que as atualizações e aplicações para transferir. Para obter informações sobre as definições disponíveis, consulte [definições de otimização de entrega para o Intune](delivery-optimization-settings.md).

4. Quando terminar, selecione **OK** > **criar** para guardar as alterações.

O perfil é criado e é apresentado na lista. Em seguida, [atribuir o perfil](device-profile-assign.md) e, em seguida [monitorizar o estado](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Mover cadências de atualização existente para otimização de entrega

**Otimização de entrega** substituir as definições **atualizações de Software-Cadências de atualização do Windows 10**. Os anéis de atualização existente podem ser facilmente alterados para utilizar o **Otimização da entrega** definições. Para tal:

1. Crie um perfil de configuração de otimização de entrega:

    1. No Intune, selecione **configuração do dispositivo** > **perfis** > **criar perfil**.
    2. Introduza as seguintes propriedades:

        - **Nome**: Introduza um nome descritivo para o novo perfil.
        - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
        - **Plataforma**: Selecione **Windows 10 e posterior**.
        - **Tipo de perfil**: Selecione **Otimização da entrega**.
        - **Definições**: Para **modo de transferência de otimização de entrega**, escolha o mesmo modo, utilizado pelo anel de atualização de software existente. As opções são:
            - **Não configurado**
            - **HTTP apenas, sem peering**
            - **HTTP aliado a peering atrás da mesma NAT**
            - **HTTP aliado a peering entre um grupo privado**
            - **HTTP aliado a peering de Internet**
            - **Modo de transferência simples sem peering**
            - **Ignorar modo**
    3. Configure definições adicionais que poderá querer gerir.
2. Atribua este perfil de novo para os mesmos dispositivos e utilizadores como o anel de atualização de software existente. [Atribuir o perfil](device-profile-assign.md) lista os passos.

3. Anular a configuração de anel de software existente:
    1. No Intune, aceda a **atualizações de Software** > Cadências de atualização do Windows 10.
    2. Na lista, selecione a cadência de atualização.
    3. Nas definições, defina **modo de transferência de otimização de entrega** ao **não configurada**.
    4. **OK** > **guardar** as suas alterações.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md) seu status.  
Ver os [definições de otimização de entrega](delivery-optimization-settings.md) para o Intune.
