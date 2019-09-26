---
title: Inscrever dispositivos Android no Intune
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dcde377dbf3e97e94957ab5c984aa6dfede9136
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71303930"
---
# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador do Intune, você pode registrar dispositivos Android das seguintes maneiras:
- Android Enterprise (oferecendo um conjunto de opções de registro que fornecem aos usuários os recursos mais atualizados e seguros):
    - [**Perfil de trabalho do Android Enterprise**](android-work-profile-enroll.md): Para dispositivos pessoais concedeu permissão para acessar dados corporativos. Os administradores podem gerenciar contas de trabalho, aplicativos e dados. Os dados pessoais no dispositivo são mantidos separados dos dados de trabalho e os administradores não controlam as configurações ou os dados pessoais. 
    - [**Android Enterprise dedicado**](android-kiosk-enroll.md): Para dispositivos corporativos, de uso único, como pôsteres digitais, impressão de tíquete ou gerenciamento de estoque. Os administradores bloqueiam a utilização de um conjunto limitado de aplicações e ligações Web num dispositivo. Além disso, também impede os utilizadores de adicionarem outras aplicações ou de efetuarem outras ações no dispositivo.
    - [**Android Enterprise totalmente gerenciado**](android-fully-managed-enroll.md): Para dispositivos de usuário único e de propriedade corporativa usados exclusivamente para trabalho e não para uso pessoal. Os administradores podem gerenciar todo o dispositivo e impor controles de política indisponíveis para perfis de trabalho. 
- [**Administrador de dispositivo Android**](android-enroll-device-administrator.md), incluindo dispositivos Samsung Knox Standard e [dispositivos pretas](android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Pré-requisitos

Para se preparar para gerir dispositivos móveis, tem de definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**. Veja [Set the MDM authority (Definir a autoridade de MDM)](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.

Para dispositivos fabricados pelo pretas Technologies, talvez seja necessário conceder a Portal da Empresa permissões adicionais dependendo dos recursos do dispositivo específico. [As extensões de mobilidade em dispositivos pretas](android-zebra-mx-overview.md) têm mais detalhes.

Para dispositivos Samsung Knox Standard, há [mais pré-requisitos](android-samsung-knox-mobile-enroll.md).

## <a name="next-steps"></a>Passos seguintes

- [Configurar registros de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md)
- [Configurar registros de dispositivo dedicado ao Android Enterprise](android-kiosk-enroll.md)
- [Configurar registros totalmente gerenciados do Android Enterprise](android-fully-managed-enroll.md)
- [Configurar o registro de administrador do dispositivo Android](android-enroll-device-administrator.md)

