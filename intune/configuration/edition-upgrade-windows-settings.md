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
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c34f683bfd16362dfb9af9a69c6f7d9b04860c7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71730716"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Configurações do dispositivo Windows 10 (e mais recente) para atualizar edições ou habilitar o modo S no Intune

O Microsoft Intune inclui muitas configurações para ajudar a gerenciar e proteger seus dispositivos. Este artigo lista e descreve as configurações para atualizar edições ou habilitar o modo S em dispositivos Windows 10. Essas configurações são criadas em um perfil de configuração de atualização no Intune que são enviadas por Push ou implantadas em dispositivos.

Como parte da sua solução de MDM (gerenciamento de dispositivo móvel), use essas configurações para controlar as opções de edição e de modo S para seus dispositivos Windows 10.

Para obter mais informações sobre esse recurso, consulte [atualizar as edições do Windows 10 ou habilitar o modo S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Antes de começar

[Crie o perfil](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Atualização de edição

- **Edição para a qual atualizar**: Selecione a edição do Windows 10 para a qual você está atualizando. Os dispositivos visados por esta política são atualizados para a edição que escolher.
- **Chave do produto**: Insira a chave do produto que você recebeu da Microsoft. Depois de criar a política que contém a chave de produto, a chave não pode ser atualizada e é ocultada por motivos de segurança. Para alterar a chave de produto, introduza novamente a chave completa.
- **Arquivo de licença**: Para **Windows 10 Holographic for Business** ou **Windows 10 Mobile Edition**, escolha **procurar** para selecionar o arquivo de licença que você recebeu da Microsoft. Esse arquivo de licença inclui informações de licença para as edições para as quais você está atualizando os dispositivos.

## <a name="mode-switch"></a>Opção de modo

- **Nenhuma configuração**: Um dispositivo de modo S permanece no modo S. Um utilizador final pode retirar o dispositivo do modo S.
- **Manter no modo S**: Desabilita o usuário final de alternar o dispositivo para fora do modo S.
- **Opção**: Alterna o dispositivo do modo S.

## <a name="next-steps"></a>Passos seguintes

O perfil é criado, mas talvez ainda não esteja fazendo nada. Certifique-se de [atribuir o perfil](device-profile-assign.md)e [monitore seu status](device-profile-monitor.md).

Você também pode criar perfis de atualização de edição para dispositivos [Windows Holographic for Business](holographic-upgrade.md) .
