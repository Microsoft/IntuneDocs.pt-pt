---
title: Atualização do Windows 10 e definições do modo de S no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições e o que fazer quando atualizar uma edição do Windows 10 num dispositivo ou ativar o modo de S num dispositivo com um perfil de configuração do dispositivo no Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c34f683bfd16362dfb9af9a69c6f7d9b04860c7
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042186"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Definições de dispositivo de 10 (e versões posteriores) do Windows para edições de atualização ou ative S o modo no Intune

O Microsoft Intune inclui várias configurações para ajudar a gerir e proteger os seus dispositivos. Este artigo apresenta uma lista e descreve as definições para atualizar as edições ou ativar o modo de S em dispositivos Windows 10. Estas definições são criadas num perfil de configuração de atualização no Intune, que são emitidos via push ou implementadas nos dispositivos.

Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para controlar as opções de modo de S para os seus dispositivos Windows 10 e a edição.

Para obter mais informações sobre esta funcionalidade, consulte [edições de atualizar o Windows 10 ou ative o S o modo](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar o perfil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Atualização de edição

- **Edição a atualizar**: Selecione a edição do Windows 10 que estiver a atualizar para. Os dispositivos visados por esta política são atualizados para a edição que escolher.
- **Chave de produto**: Introduza a chave de produto que recebeu da Microsoft. Depois de criar a política que contém a chave de produto, a chave não pode ser atualizada e é ocultada por motivos de segurança. Para alterar a chave de produto, introduza novamente a chave completa.
- **Ficheiro de licença**: Para **Windows 10 Holographic for Business** ou **edition do Windows 10 Mobile**, escolha **procurar** para selecionar o ficheiro de licença que recebeu da Microsoft. Este ficheiro de licença inclui informações de licença para as edições que estiver a atualizar os dispositivos.

## <a name="mode-switch"></a>Comutador de modo

- **Nenhuma configuração**: Um dispositivo de modo S permanece no modo de S. Um utilizador final pode retirar o dispositivo do modo S.
- **Tenha em modo de S**: Desativa o utilizador final alternem o dispositivo sair do modo de S.
- **Comutador**: Muda o dispositivo sair do modo de S.

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas ele pode não fazer nada ainda. Não se esqueça [atribuir o perfil](device-profile-assign.md), e [monitorizar o estado](device-profile-monitor.md).

Também pode criar edição de perfis de atualização para [Windows Holographic for Business](holographic-upgrade.md) dispositivos.
