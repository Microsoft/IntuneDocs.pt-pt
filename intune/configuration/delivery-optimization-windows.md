---
title: Definições de otimização de entrega para windows 10 no Microsoft Intune - Azure Microsoft Docs
description: Configure como os dispositivos do Windows 10 gere com a otimização da entrega de utilização intune. Em Intune, crie um perfil de configuração do dispositivo para instalar atualizações a partir da internet. Consulte também como substituir os anéis de atualização existentes por um perfil de otimização de entrega.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369948"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Definições de otimização de entrega no Microsoft Intune

Com o Intune, utilize as definições de Otimização de Entrega para os dispositivos Windows 10 para reduzir o consumo de largura de banda quando esses dispositivos descarregarem aplicações e atualizações. Configure a otimização da entrega como parte dos perfis de configuração do seu dispositivo.  

Este artigo descreve como configurar as definições de otimização de entrega como parte de um perfil de configuração do dispositivo. Depois de criar um perfil, atribui ou implementa esse perfil para os seus dispositivos Windows 10. 

Para ver uma lista das definições de otimização de entrega que o Intune suporta, consulte as definições de [Otimização de Entrega para Intune](../delivery-optimization-settings.md).  

Para saber mais sobre a Otimização de Entregas no Windows 10, consulte [as atualizações](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) de Otimização de Entrega na documentação do Windows.  

## <a name="create-the-profile"></a>Criar o perfil

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** > **Criar perfil**.

3. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o novo perfil.
    - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione **o Windows 10 e mais tarde**.
    - **Tipo de perfil**: Selecione **otimização de entrega**.

4. Escolha **Definições** > **Configurar**e defina como pretende que as atualizações e aplicações descarreguem. Para obter informações sobre as definições disponíveis, consulte [as definições de otimização da entrega para Intune](../delivery-optimization-settings.md).

5. Quando terminar, selecione **OK** > **Criar** para guardar as alterações.

O perfil é criado e é mostrado na lista. Em seguida, [atribua o perfil](device-profile-assign.md) e, em [seguida, monitorize o seu estado](device-profile-monitor.md).

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Remover otimização de entrega dos anéis de atualização do Windows 10

A Otimização da Entrega foi previamente configurada como parte dos Anéis de Atualização de Software. A partir de fevereiro de 2019, as definições de Otimização de Entrega são configuradas como parte de um perfil de configuração de dispositivo de otimização de deliver, que inclui configurações adicionais que afetam mais do que a entrega de Atualizações de Software para dispositivos. Se ainda não o fez, remova a definição de otimização de entrega dos seus Anéis de Atualização, definindo-a para *Não configurada,* e depois utilize um perfil de Otimização de Entrega para gerir a maior gama de opções disponíveis.

1. Criar um perfil de configuração do dispositivo de otimização de entrega:

    1. No centro de administração do Microsoft Endpoint Manager, selecione **Dispositivos** > perfis de **configuração** > **Criar perfil**.
    2. Introduza as seguintes propriedades:

        - **Nome**: introduza um nome descritivo para o novo perfil.
        - **Descrição:** introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
        - **Plataforma**: Selecione **o Windows 10 e mais tarde**.
        - **Tipo de perfil**: Selecione **otimização de entrega**.
        - **Definições**: Para o modo de transferência de otimização da **entrega,** escolha o mesmo modo que é utilizado pelo anel de atualização de software existente, a menos que pretenda alterar as definições que aplica nos seus dispositivos. As opções são:
            - **Não configurado**
            - **Apenas HTTP, sem espreitar**
            - **HTTP misturado com o olhar atrás do mesmo NAT**
            - **HTTP misturado com olhing em um grupo privado**
            - **HTTP misturado com o peering da Internet**
            - **Modo de descarregamento simples sem espreitar**
            - **Modo bypass**
    3. Configure quaisquer definições adicionais que queira gerir.

2. Atribuir este novo perfil aos mesmos dispositivos e utilizadores que o anel de atualização de software existente. [Atribuir o perfil](device-profile-assign.md) lista os passos.

3. Desconfigure o anel de software existente:
    1. No centro de administração do Microsoft Endpoint Manager, vá a **atualizações** de Software > Windows 10 Update Rings.
    2. Na lista, selecione o seu anel de atualização.
    3. Nas definições, desajuste o modo de transferência de **otimização** da entrega para **Não configurado**.
    4. **OK** > **Guarde** as suas alterações.

## <a name="next-steps"></a>Próximos passos

[Atribuir o perfil](device-profile-assign.md) e [monitorizar o seu estado.](device-profile-monitor.md)  
Consulte as definições de [otimização](../delivery-optimization-settings.md) da entrega para Intune.
