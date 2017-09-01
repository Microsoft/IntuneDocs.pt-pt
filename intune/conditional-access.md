---
title: Acesso condicional com o Intune
titleSuffix: Intune on Azure
description: "Saiba como definir as condições que os utilizadores e os dispositivos têm de reunir para aceder aos recursos da empresa no Microsoft Intune.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f6f7443224b9ec114f0323d1715f343b0adfec4
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2017
---
# <a name="whats-conditional-access"></a>O que é o acesso condicional?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico descreve o Acesso condicional e de que forma se aplica ao Enterprise Mobility + Security (EMS) e, em seguida, os cenários comuns de Acesso condicional na utilização o do Intune.

O Acesso Condicional do Enterprise Mobility + Security (EMS) não é um produto autónomo, mas sim uma solução que participa de todos os serviços e produtos que fazem parte do EMS. Fornece controlo de acesso granular para proteger os dados da sua empresa e, em simultâneo, proporciona aos utilizadores uma experiência que lhes permita realizar o seu melhor trabalho a partir de qualquer dispositivo e de qualquer local.

Pode definir as condições para o acesso de porta aos dados da sua empresa com base na localização, no dispositivo, no estado do utilizador e na sensibilidade das aplicações.

> [!NOTE] 
> Além disso, o Acesso Condicional expande as suas capacidades a [serviços do Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagrama da arquitetura do acesso condicional](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Acesso condicional com o Intune

O Intune adiciona políticas de conformidade do dispositivo móvel e gestão de aplicações para suportar a solução de Acesso Condicional do EMS.

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

## <a name="next-steps"></a>Próximos passos

[Formas comuns de utilizar o acesso condicional com o Intune](conditional-access-intune-common-ways-use.md)