---
title: Acesso condicional com Microsoft Intune
titleSuffix: Microsoft Intune
description: Saiba como definir as condições que os utilizadores, dispositivos e aplicações têm de reunir para aceder aos recursos da empresa no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cef8bcf74509d83b076b30a1ee7f2406e622b129
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71729748"
---
# <a name="learn-about-conditional-access-and-intune"></a>Saiba mais sobre o acesso condicional e o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O acesso condicional refere-se a maneiras que você pode controlar os dispositivos e aplicativos que têm permissão para se conectar ao seu email e aos recursos da empresa. Neste tópico, saiba mais sobre o acesso condicional baseado em dispositivo e com base no aplicativo e encontre cenários comuns para usar o acesso condicional com o Intune.

O Acesso Condicional do Enterprise Mobility + Security (EMS) não é um produto autónomo, mas sim uma solução que participa de todos os serviços e produtos que fazem parte do EMS. Fornece controlo de acesso granular para proteger os dados da sua empresa e, em simultâneo, proporciona aos utilizadores uma experiência que lhes permita realizar o seu melhor trabalho a partir de qualquer dispositivo e de qualquer local.

Pode definir as condições para o acesso de porta aos dados da sua empresa com base na localização, no dispositivo, no estado do utilizador e na sensibilidade das aplicações.

> [!NOTE] 
> Além disso, o Acesso Condicional expande as suas capacidades a [serviços do Office 365](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access).

![Diagrama arquitetônico de acesso condicional](./media/conditional-access/ca-diagram-1.png)

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

## <a name="next-steps"></a>Passos seguintes

[Maneiras comuns de usar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
