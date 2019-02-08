---
title: Acesso condicional com o Microsoft Intune | Microsoft Intune
description: Saiba como definir as condições que os utilizadores, dispositivos e aplicações têm de reunir para aceder aos recursos da empresa no Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a540d47d9b4418f7cf613fa401e92463d74a17fa
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838568"
---
# <a name="whats-conditional-access"></a>O que é o acesso condicional?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O acesso condicional refere-se às formas como pode controlar os dispositivos e aplicações que têm permissão para se ligarem ao seu e-mail e recursos da empresa. Neste tópico, saiba mais sobre o acesso condicional baseado em dispositivos e baseado em aplicações e descubra cenários comuns para utilizar o acesso condicional com o Intune.

O Acesso Condicional do Enterprise Mobility + Security (EMS) não é um produto autónomo, mas sim uma solução que participa de todos os serviços e produtos que fazem parte do EMS. Fornece controlo de acesso granular para proteger os dados da sua empresa e, em simultâneo, proporciona aos utilizadores uma experiência que lhes permita realizar o seu melhor trabalho a partir de qualquer dispositivo e de qualquer local.

Pode definir as condições para o acesso de porta aos dados da sua empresa com base na localização, no dispositivo, no estado do utilizador e na sensibilidade das aplicações.

> [!NOTE] 
> Além disso, o Acesso Condicional expande as suas capacidades a [serviços do Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagrama da arquitetura do acesso condicional](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Acesso condicional com o Intune

O acesso condicional é uma funcionalidade do Azure Active Directory incluída com uma licença do Azure Active Directory Premium. O Intune melhora esta funcionalidade ao adicionar à solução a conformidade de dispositivos móveis e a gestão de aplicações móveis. 

![Intune e acesso condicional na utilização do EMS](./media/intune-with-ca-1.png)

Formas de utilizar o acesso condicional com o Intune:

-   **Acesso condicional baseado no dispositivo**

    -   Acesso condicional para o Exchange no local

    -   Acesso condicional com base no controlo de acesso de rede

    -   Acesso condicional com base no risco do dispositivo

    -   Acesso condicional para PCs Windows

        -   Pertencentes à empresa

        -   Bring your own device (BYOD)

-   **Acesso condicional com base nas aplicações**

## <a name="next-steps"></a>Passos Seguintes

[Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)
