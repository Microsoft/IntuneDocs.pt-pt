---
title: Acesso condicional com o Intune
titlesuffix: Azure portal
description: "Saiba como definir as condições que os utilizadores e os dispositivos têm de reunir para aceder aos recursos da empresa no Microsoft Intune.\""
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4d3d84f8010b72b9595f3ff54924d6c3fe245702
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
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
