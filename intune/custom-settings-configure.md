---
title: Utilizar definições personalizadas do dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar um perfil para usar configurações personalizadas para os dispositivos Windows Phone, Windows 8.1, Windows 10 e posterior, Android, Android Enterprise, macOS e iOS usando o Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 854e8fc7a46f431ce36c4e30682c196e6484b93e
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163119"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Criar um perfil com definições personalizadas no Intune

## <a name="what-are-custom-profiles"></a>O que são perfis personalizados

O Microsoft Intune inclui várias definições incorporadas para controlar diferentes funcionalidades num dispositivo. Também pode criar perfis personalizados. Os perfis personalizados são úteis se pretender utilizar definições e funcionalidades de dispositivos que não estão incorporadas no Intune. Estes perfis incluem funcionalidades e definições que pode controlar em dispositivos na sua organização. Por exemplo, pode criar um perfil personalizado que define a mesma funcionalidade para todos os dispositivos iOS.

Para obter mais informações sobre perfis de configuração, veja [O que são os perfis de dispositivos do Microsoft Intune?](device-profiles.md) 

Este artigo contém ligações para criar perfis personalizados no Android, Android Enterprise, iOS, macOS e Windows.

## <a name="available-platforms"></a>Plataformas disponíveis

As definições personalizadas são configuradas de forma diferente para cada plataforma. Por exemplo, para controlar as funcionalidades em dispositivos Android e Windows, pode introduzir valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI). Para dispositivos Apple, pode importar um ficheiro que criou no [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) ou no [Gestor de Perfis da Apple](https://support.apple.com/profile-manager).

Os perfis personalizados são criados de forma semelhante à dos perfis incorporados e estão disponíveis nas seguintes plataformas:

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Passos seguintes

Selecione a sua plataforma para começar:

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
