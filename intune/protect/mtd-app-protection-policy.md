---
title: Criar política de proteção de aplicações mobile threat defense (MTD) com Intune
titleSuffix: Microsoft Intune
description: Crie a política de proteção de aplicações Mobile Threat Defense (MTD) com a Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
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
ms.openlocfilehash: 900858d9c437f2d2662260ca62534a987446d2b2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782118"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Criar política de proteção de aplicações de defesa de ameaças móveis com Intune

Intune with Mobile Threat Defense (MTD) ajuda-o a detetar ameaças e a avaliar o risco em dispositivos móveis. Pode criar uma política de proteção de aplicações Intune que avalie o risco para determinar se o dispositivo está autorizado a aceder ou não a dados corporativos.

> [!NOTE]
> Este artigo aplica-se a todos os parceiros de Defesa de Ameaças Móveis que apoiam políticas de proteção de aplicações:
>
> - Melhor Móvel (Android, iOS/iPadOS)
> - Zimperium (Android, iOS/iPadOS)
> - Procura de trabalho (Android, iOS/iPadOS).

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Agora precisa de definir o nível de Defesa de Ameaças Móveis na política de proteção de aplicações Intune.

Pré-requisitos para a política de proteção de aplicações com MTD:

- Instale a integração do MTD com o Intune. Sem esta integração, a política de proteção de aplicações MTD não terá qualquer efeito.

## <a name="to-create-an-mtd-app-protection-policy"></a>Para criar uma política de proteção de aplicações MTD

Utilize o procedimento para criar uma política de proteção de [aplicações para iOS/iPadOS ou Android,](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps)e utilize as seguintes informações sobre as *páginas Apps,* *Lançamento Condicional*e *Atribuição:*

- **Aplicativos**: Selecione as aplicações que deseja ser alvo de políticas de proteção de aplicações. Para este conjunto de funcionalidades, estas aplicações são bloqueadas ou limpas seletivamente com base na avaliação de risco do dispositivo do seu fornecedor de Defesa de Ameaças Móveis escolhido.
- **Lançamento condicional**: Abaixo as *condições*do dispositivo , utilize a caixa de drop-down para selecionar **o nível de ameaça do dispositivo Max .**

  Opções para o nível de ameaça **Valor:**

  - **Seguro**: este é o nível mais seguro. O dispositivo não pode ter ameaças presentes e ainda aceder aos recursos da empresa. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.
  - **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.
  - **Alto**: Este nível é o menos seguro e permite todos os níveis de ameaça, usando a defesa de ameaças móveis apenas para fins de reporte. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

  Opções de **Ação:**

  - **Bloquear acesso**
  - **Limpar dados**

- **Atribuições**: Atribuir a política a grupos de utilizadores.  Os dispositivos utilizados pelos membros do grupo são avaliados para acesso a dados corporativos em aplicações direcionadas através da proteção de aplicações Intune.

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre [a Defesa de Ameaças Móveis](~/protect/mobile-threat-defense.md) no Microsoft Intune.
