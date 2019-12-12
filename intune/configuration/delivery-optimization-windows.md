---
title: Configurações de otimização de entrega para Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Configure como os dispositivos Windows 10 gerenciados com o Intune usam a otimização de entrega. No Intune, crie um perfil de configuração de dispositivo para instalar atualizações da Internet. Consulte também como substituir os anéis de atualização existentes por um perfil de otimização de entrega.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 44078f61e4f1939b1f0b15b3dde5ac54938ffbc3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059968"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Configurações de otimização de entrega no Microsoft Intune

Com o Intune, você pode usar as configurações de otimização de entrega para seus dispositivos Windows 10 para reduzir o consumo de largura de banda quando esses dispositivos baixam aplicativos e atualizações. A otimização de entrega é configurada como parte dos perfis de configuração do dispositivo.  

Este artigo descreve como definir as configurações de otimização de entrega como parte de um perfil de configuração de dispositivo. Depois de criar um perfil, atribua ou implante esse perfil em seus dispositivos Windows 10. 

Para obter uma lista das configurações de otimização de entrega às quais o Intune dá suporte, consulte [configurações de otimização de entrega para o Intune](../delivery-optimization-settings.md).  

Para saber mais sobre a otimização de entrega no Windows 10, consulte [atualizações de otimização de entrega](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) na documentação do Windows.  

> [!NOTE]
> **Atualizações de software – os anéis de atualização do Windows 10** são substituídos pelas configurações de **otimização de entrega** . Os anéis de atualização existentes podem ser alterados para usar as configurações de **otimização de entrega** . [Mover os anéis de atualização existentes para a otimização de entrega](#move-existing-update-rings-to-delivery-optimization) (neste artigo)

## <a name="create-the-profile"></a>Criar o perfil

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: selecione **Windows 10 e posterior**.
    - **Tipo de perfil**: selecione **otimização de entrega**.

4. Escolha **configurações** > **Configurar**e defina como deseja que as atualizações e os aplicativos sejam baixados. Para obter informações sobre as configurações disponíveis, consulte [configurações de otimização de entrega para o Intune](../delivery-optimization-settings.md).

5. Quando terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e é mostrado na lista. Em seguida, [atribua o perfil](device-profile-assign.md) e [monitore seu status](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Mover os anéis de atualização existentes para a otimização de entrega

Configurações de **otimização de entrega** substituir **atualizações de software – anéis de atualização do Windows 10**. Seus anéis de atualização existentes podem ser facilmente alterados para usar as configurações de **otimização de entrega** . Para manter as mesmas configurações ao criar um perfil de otimização de entrega, use o mesmo *modo de download de otimização de entrega* e defina as mesmas configurações que você já usa. No entanto, você pode optar por reconfigurar as configurações de otimização de entrega para tirar proveito da gama completa de configurações de adição que o perfil de otimização de entrega pode gerenciar.

1. Criar um perfil de configuração de otimização de entrega:

    1. No centro de administração do Microsoft Endpoint Manager, selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.
    2. Introduza as seguintes propriedades:

        - **Nome**: introduza um nome descritivo para o novo perfil.
        - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
        - **Plataforma**: selecione **Windows 10 e posterior**.
        - **Tipo de perfil**: selecione **otimização de entrega**.
        - **Configurações**: para o **modo de download da otimização de entrega**, escolha o mesmo modo usado pelo anel de atualização de software existente, a menos que você queira alterar as configurações aplicadas aos seus dispositivos. As opções são:
            - **Não configurado**
            - **Somente HTTP, sem emparelhamento**
            - **HTTP combinado com emparelhamento por trás do mesmo NAT**
            - **HTTP combinado com emparelhamento em um grupo privado**
            - **HTTP combinado com emparelhamento da Internet**
            - **Modo de download simples sem emparelhamento**
            - **Modo de bypass**
    3. Defina as configurações adicionais que você pode desejar gerenciar.

2. Atribua esse novo perfil aos mesmos dispositivos e usuários que o anel de atualização de software existente. [Atribuir o perfil](device-profile-assign.md) lista as etapas.

3. Desconfigure o anel de software existente:
    1. No centro de administração do Microsoft Endpoint Manager, acesse **atualizações de Software** > anéis de atualização do Windows 10.
    2. Na lista, selecione o anel de atualização.
    3. Nas configurações, defina o **modo de download de otimização de entrega** como **não configurado**.
    4. **OK** > **salvar** suas alterações.

## <a name="next-steps"></a>Próximos passos

[Atribua o perfil](device-profile-assign.md) e [monitore seu](device-profile-monitor.md) status.  
Exiba as [configurações de otimização de entrega](../delivery-optimization-settings.md) para o Intune.
