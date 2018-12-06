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
ms.openlocfilehash: 1b83a380620704e9e3f616cee77b33d577c86c0d
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977274"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Definições de otimização de entrega de 10 (e versões posteriores) do Windows no Microsoft Intune

Este artigo apresenta e descreve todas as definições de otimização de entrega que pode configurar para dispositivos Windows 10. Estas definições são adicionadas a um perfil de configuração do dispositivo e, em seguida, atribuídas ou implementadas nos seus dispositivos com o Microsoft Intune. 

[Otimização da entrega de atualizações](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) é um ótimo recurso para obter mais informações sobre a otimização de entrega no Windows 10.

## <a name="settings"></a>Definições

**Modo de transferência de otimização de entrega**: Escolha a forma como as atualizações são disponibilizadas para os seus dispositivos. As opções são:

- **Não configurado**: os utilizadores finais atualizar seus dispositivos com seus próprios métodos, que podem estar a utilizar o **atualizações do Windows** ou **Otimização da entrega** definições disponíveis com o sistema operacional.
- **HTTP apenas, sem peering**: obter atualizações apenas a partir da internet. Não obter atualizações a partir de outros computadores na sua rede (chamado de peering ou ponto-a-ponto).
- **HTTP aliado a peering atrás da mesma NAT HTTP aliado a peering entre um grupo privado**: obter atualizações da internet e de outros computadores na sua rede. Peering ocorre em dispositivos do mesmo Site do Active Directory (se existir) ou o mesmo domínio. Quando esta opção está selecionada, peering cruza os endereços IP de tradução de endereços de rede (NATs).
- **HTTP aliado a peering de Internet**: obter atualizações da internet e de outros computadores na sua rede.
- **Modo de transferência simples sem peering**: obtém as atualizações a partir da internet, diretamente a partir do proprietário da atualização, como o Microsoft. Não contacta os serviços de cloud de otimização de entrega.
- **O modo ignorar**: utilização em segundo plano inteligente serviço de transferência (BITS) para obter atualizações. Não utilize a Otimização da entrega.

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>Mover de cadências de atualização existente para otimização de entrega

**Atualizações de software-Cadências de atualização do Windows 10** são substituídos pela **Otimização da entrega** definições. Os anéis de atualização existente podem ser facilmente alterados para utilizar o **Otimização da entrega** definições. passos:

1. Crie um perfil de configuração de otimização de entrega:

    1. No Intune, selecione **configuração do dispositivo** > **perfis** > **criar perfil**.
    2. Introduza um **Nome** e uma **Descrição** para o perfil.
    3. Para **plataforma**, escolha **Windows 10 e posterior**. Para **tipo de perfil**, escolha **Otimização da entrega**.
    4. Selecione **Definições**. Para **modo de transferência de otimização de entrega**, escolha o mesmo modo, utilizado pelo anel de atualização de software existente. As opções são:
        - **Não configurado**
        - **HTTP apenas, sem peering**
        - **HTTP aliado a peering atrás da mesma NAT HTTP aliado a peering entre um grupo privado**
        - **HTTP aliado a peering de Internet**
        - **Modo de transferência simples sem peering**
        - **Ignorar modo**

2. Atribua este perfil de novo para os mesmos dispositivos e utilizadores como o anel de atualização de software existente. [Atribuir o perfil](device-profile-assign.md) lista os passos.

3. Anular a configuração de anel de software existente:
    1. No Intune, aceda a **atualizações de Software** > Cadências de atualização do Windows 10.
    2. Na lista, selecione a cadência de atualização.
    3. Nas definições, defina o **modo de transferência de otimização de entrega** ao **não configurada**.
    4. **OK** > **guardar** as suas alterações.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir o perfil](device-profile-assign.md) e [monitorizar o estado](device-profile-monitor.md) seu status.
