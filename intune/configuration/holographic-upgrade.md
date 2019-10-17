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
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6342ed23f67c37c2f5084e58594294d826a28e40
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506712"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Atualizar os dispositivos com o Windows Holographic para o Windows Holographic for Business

O Microsoft Intune inclui muitas configurações para ajudar a gerenciar e proteger seus dispositivos. Este artigo lista e descreve as configurações para atualizar dispositivos Windows Holographic para o Windows Holographic for Business. Essas configurações são criadas em um perfil de configuração de atualização no Intune que são enviadas por Push ou implantadas em dispositivos.

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para atualizar seus dispositivos Windows Holographic. Para o Microsoft HoloLens, você pode comprar o pacote comercial para obter a licença necessária para a atualização. Para obter mais informações, veja [Desbloquear as funcionalidades do Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens1-upgrade-enterprise).

Para obter mais informações sobre esse recurso, consulte [atualizar as edições do Windows 10 ou habilitar o modo S](../edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar um perfil de configuração de dispositivo](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Atualização de edição

- **Edição**para a qual atualizar: selecione **Windows 10 Holographic for Business**.
- **Arquivo de licença**: Navegue até e selecione o arquivo de licença XML que foi fornecido a você.

  ![Insira o nome do arquivo XML que inclui as informações de licença do Holographic for Business](./media/holographic-upgrade/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas talvez ainda não esteja fazendo nada. Certifique-se de [atribuir o perfil](device-profile-assign.md)e [monitore seu status](../device-profile-monitor.md).

Você também pode criar perfis de atualização de edição para dispositivos [Windows 10 e posteriores](edition-upgrade-windows-settings.md) .
