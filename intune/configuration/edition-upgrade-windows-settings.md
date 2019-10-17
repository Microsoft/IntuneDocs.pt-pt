---
title: Atualização do Windows 10 e configurações de modo S no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as configurações e o que elas fazem ao atualizar uma edição do Windows 10 em um dispositivo ou habilitar o modo S em um dispositivo usando um perfil de configuração de dispositivo no Microsoft Intune.
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
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75878e2110e9d855c2a0f78c0e7a1112f883872e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72489655"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Configurações do dispositivo Windows 10 (e mais recente) para atualizar edições ou habilitar o modo S no Intune

O Microsoft Intune inclui muitas configurações para ajudar a gerenciar e proteger seus dispositivos. Este artigo lista e descreve as configurações para atualizar edições ou habilitar o modo S em dispositivos Windows 10. Essas configurações são criadas em um perfil de configuração de atualização no Intune que são enviadas por Push ou implantadas em dispositivos.

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para controlar as opções de edição e de modo S para seus dispositivos Windows 10.

Para obter mais informações sobre esse recurso, consulte [atualizar as edições do Windows 10 ou habilitar o modo S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie o perfil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Atualização de edição

- **Edição a atualizar**: selecione a edição Windows 10 para a qual está a atualizar. Os dispositivos visados por esta política são atualizados para a edição que escolher.
- **Chave de Produto**: introduza a chave de produto que recebeu da Microsoft. Depois de criar a política que contém a chave de produto, a chave não pode ser atualizada e é ocultada por motivos de segurança. Para alterar a chave de produto, introduza novamente a chave completa.
- **Ficheiro de Licença**: para **Windows 10 Holographic for Business** ou **Edição Windows 10 Mobile**, selecione **Procurar** para selecionar o ficheiro de licença que recebeu da Microsoft. Esse arquivo de licença inclui informações de licença para as edições para as quais você está atualizando os dispositivos.

## <a name="mode-switch"></a>Opção de modo

- **Sem configuração**: um dispositivo de modo s permanece no modo s. Um utilizador final pode retirar o dispositivo do modo S.
- **Manter no modo S**: não permite ao utilizador final retirar o dispositivo do modo S.
- **Alterar**: retira o dispositivo do modo S.

## <a name="next-steps"></a>Próximos passos

O perfil é criado, mas talvez ainda não esteja fazendo nada. Certifique-se de [atribuir o perfil](device-profile-assign.md)e [monitore seu status](device-profile-monitor.md).

Você também pode criar perfis de atualização de edição para dispositivos [Windows Holographic for Business](holographic-upgrade.md) .
