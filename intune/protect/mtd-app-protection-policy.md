---
title: Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com o Intune
titleSuffix: Microsoft Intune
description: Criar política de proteção de aplicativo MTD (defesa contra ameaças móveis) com Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48dc7de86965741d8ed42bd5a5f29f72ae66d4f3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188504"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Criar política de proteção do aplicativo de defesa contra ameaças móveis com o Intune

O Intune com defesa contra ameaças móveis (MTD) ajuda você a detectar ameaças e avaliar o risco em dispositivos móveis. Você pode criar uma política de proteção de aplicativo do Intune que avalia o risco para determinar se o dispositivo tem permissão para acessar dados corporativos ou não.


> [!NOTE]
> Este artigo se aplica a todos os parceiros de defesa contra ameaças móveis que dão suporte a políticas de proteção de aplicativo:
>
> - Melhores dispositivos móveis (Android)
> - Zimperium (iOS)
> - Lookout for Work (Android, iOS).

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Agora você precisa definir o nível de defesa contra ameaças móveis na política de proteção de aplicativo do Intune.

Pré-requisitos para a política de proteção de aplicativo com MTD:

- Configure a integração do MTD com o Intune. Sem essa integração, a política de proteção do aplicativo MTD não terá nenhum efeito.

## <a name="to-create-an-mtd-app-protection-policy"></a>Para criar uma política de proteção de aplicativo MTD

Use o procedimento para [criar uma política de proteção de aplicativo para o Ios/iPadOS ou Android](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps)e use as seguintes informações nas páginas *aplicativos*, *inicialização condicional*e *atribuições* :

- **Aplicativos**: selecione o aplicativo para o parceiro de defesa contra ameaças móveis que você usa.
- **Inicialização condicional**: abaixo das *condições do dispositivo*, use a caixa suspensa para selecionar o **nível máximo de ameaça do dispositivo permitido**.

  Opções para o **valor**de nível de ameaça:

  - **Seguro**: este é o nível mais seguro. O dispositivo não pode ter nenhuma ameaça presente e ainda acessar os recursos da empresa. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.
  - **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
  - **Elevado**: este é o nível menos seguro. Isso permite todos os níveis de ameaça e usa a defesa contra ameaças móveis apenas para fins de relatório. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

  Opções para **ação**:

  - **Bloquear acesso**
  - **Apagar dados**

- **Atribuições**: atribuir a política a grupos de usuários.  Os dispositivos usados pelos membros do grupo são avaliados para acesso a dados corporativos em aplicativos de destino por meio da proteção de aplicativo do Intune.


## <a name="next-steps"></a>Próximos passos  

- Saiba mais sobre a [defesa contra ameaças móveis](~/protect/mobile-threat-defense.md) em Microsoft Intune.
