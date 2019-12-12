---
title: Acesso condicional com Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba como definir as condições que os usuários, os dispositivos e os aplicativos devem atender para acessar os recursos da empresa no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188285"
---
# <a name="learn-about-conditional-access-and-intune"></a>Saiba mais sobre o acesso condicional e o Intune

Com o acesso condicional, você pode controlar os dispositivos e aplicativos que podem se conectar ao seu email e aos recursos da empresa. 

O EMS (Enterprise Mobility + Security) não é um produto autônomo. É uma solução que faz parte de todos os serviços e produtos que fazem parte do EMS. O acesso condicional fornece controle de acesso granular para manter seus dados corporativos seguros, oferecendo aos usuários uma experiência que permite que eles façam o melhor trabalho de qualquer dispositivo e de qualquer local.

Pode definir as condições para o acesso de porta aos dados da sua empresa com base na localização, no dispositivo, no estado do utilizador e na sensibilidade das aplicações.

> [!NOTE]
> Além disso, o Acesso Condicional expande as suas capacidades a [serviços do Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagrama de acesso condicional](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Usar o acesso condicional com o Intune

O acesso condicional é um recurso Azure Active Directory que é incluído em uma licença Azure Active Directory Premium. O Intune melhora esta funcionalidade ao adicionar à solução a conformidade de dispositivos móveis e a gestão de aplicações móveis. 

![Intune e acesso condicional ao usar o EMS](./media/conditional-access/intune-with-ca-1.png)

Maneiras de usar o acesso condicional com o Intune:

- **Acesso condicional com base no dispositivo**

  - Acesso condicional para o Exchange local

  - Acesso condicional com base no controle de acesso à rede

  - Acesso condicional com base no risco do dispositivo

  - Acesso condicional para computadores Windows

    - Pertencentes à empresa

    - Bring your own device (BYOD)

- **Acesso condicional baseado no aplicativo**

## <a name="next-steps"></a>Próximos passos

[Maneiras comuns de usar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
