---
title: Atualizar para o Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Saiba como atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c6a2f4fc3e3cae171cea96520d075a659d4d1ca
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566340"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business

O Microsoft Intune inclui várias configurações para ajudar a gerir e proteger os seus dispositivos. Este artigo apresenta uma lista e descreve as definições para atualizar dispositivos Windows Holographic para o Windows Holographic for Business. Estas definições são criadas num perfil de configuração de atualização no Intune, que são emitidos via push ou implementadas nos dispositivos.

Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para atualizar os seus dispositivos com o Windows Holographic. Para o Microsoft HoloLens, pode comprar o Commercial Suite para obter a licença necessária para a atualização. Para obter mais informações, veja [Desbloquear as funcionalidades do Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise).

Para obter mais informações sobre esta funcionalidade, consulte [edições de atualizar o Windows 10 ou ative o S o modo](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração do dispositivo](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Atualização de edição

- **Edição a atualizar**: Selecione **Windows 10 Holographic for Business**.
- **Ficheiro de licença**: Procure e selecione o ficheiro de licença XML que lhe foi fornecido.

  ![Introduza o nome do ficheiro XML que inclui o Holographic para obter informações de licença de negócios](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas ele pode não fazer nada ainda. Não se esqueça [atribuir o perfil](device-profile-assign.md), e [monitorizar o estado](device-profile-monitor.md).

Também pode criar edição de perfis de atualização para [Windows 10 e posterior](edition-upgrade-windows-settings.md) dispositivos.
