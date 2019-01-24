---
title: As definições de otimização de entrega para o Windows 10 no Microsoft Intune – Azure | Documentos da Microsoft
description: Configure a forma como as atualizações de software são entregues para os seus dispositivos com os serviços de nuvem de otimização de entrega disponíveis com o Windows 10 e dispositivos posteriores. No Intune, crie um perfil de configuração do dispositivo para instalar atualizações a partir da internet. Veja também como substituir cadências de atualização existente com um perfil de otimização de entrega.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831552"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Definições de otimização de entrega de 10 (e versões posteriores) do Windows no Microsoft Intune

> [!NOTE]
> **Atualizações de software-Cadências de atualização do Windows 10** são substituídos pela **Otimização da entrega** definições. Os anéis de atualização existente podem ser alterados para utilizar o **Otimização da entrega** definições. [Mover cadências de atualização existente para otimização de entrega](#move-existing-update-rings-to-delivery-optimization) (neste artigo) apresenta os passos. 


Esta funcionalidade aplica-se para a plataforma seguinte:

- Windows 10 e posterior

Este artigo apresenta e descreve todas as definições de otimização de entrega que pode configurar para dispositivos Windows 10. Estas definições são adicionadas a um perfil de configuração do dispositivo e, em seguida, atribuídas ou implementadas nos seus dispositivos com o Microsoft Intune.

[Otimização da entrega de atualizações](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) é um ótimo recurso para obter mais informações sobre a otimização de entrega no Windows 10.

## <a name="create-the-profile"></a>Criar o perfil

1. Na [portal do Azure](https://portal.azure.com), selecione **todos os serviços** > Filtrar **Intune** > selecione **Intune**.

2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar Perfil**.

3. Introduza as seguintes propriedades:

    - **Nome**: Introduza um nome descritivo para o novo perfil.
    - **Descrição**: Introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: Selecione a plataforma:  

        - **Windows 10 e posterior**

    - **Tipo de perfil**: Selecione **Otimização da entrega**.
    - **Definições**: Escolha como pretende que as atualizações baixadas. As opções são: 

        - **Não configurado**: Os utilizadores finais atualizar seus dispositivos com seus próprios métodos, que podem estar a utilizar o **Windows atualiza** ou **Otimização da entrega** definições disponíveis com o sistema operacional.
        - **HTTP apenas, sem peering**: Obter atualizações apenas a partir da internet. Não obter atualizações a partir de outros computadores na sua rede (chamado de peering ou ponto-a-ponto).
        - **HTTP aliado a peering atrás da mesma NAT**: Obtenha atualizações da internet e de outros computadores na sua rede. 
        - **HTTP aliado a peering entre um grupo privado**: Peering ocorre em dispositivos do mesmo Site do Active Directory (se existir) ou o mesmo domínio. Quando esta opção está selecionada, peering cruza os endereços IP de tradução de endereços de rede (NATs).
        - **HTTP aliado a peering de Internet**: Obtenha atualizações da internet e de outros computadores na sua rede.
        - **Modo de transferência simples sem peering**: Obtém as atualizações a partir da internet, diretamente a partir do proprietário da atualização, como o Microsoft. Não contacta os serviços de cloud de otimização de entrega.
        - **O modo ignorar**: Utilize o serviço de transferência inteligente em segundo plano (BITS) para obter atualizações. Não utilize a Otimização da entrega.

4. Quando terminar, selecione **OK** > **criar** para guardar as alterações.

O perfil é criado e é apresentado na lista. Em seguida, [atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Mover cadências de atualização existente para otimização de entrega

**Atualizações de software-Cadências de atualização do Windows 10** são substituídos pela **Otimização da entrega** definições. Os anéis de atualização existente podem ser facilmente alterados para utilizar o **Otimização da entrega** definições. passos:

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

2. Atribua este perfil de novo para os mesmos dispositivos e utilizadores como o anel de atualização de software existente. [Atribuir o perfil](device-profile-assign.md) lista os passos.

3. Anular a configuração de anel de software existente:
    1. No Intune, aceda a **atualizações de Software** > Cadências de atualização do Windows 10.
    2. Na lista, selecione a cadência de atualização.
    3. Nas definições, defina **modo de transferência de otimização de entrega** ao **não configurada**.
    4. **OK** > **guardar** as suas alterações.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md) seu status.
