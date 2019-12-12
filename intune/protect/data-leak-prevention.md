---
title: Impedir fugas de dados em dispositivos não geridos
titleSuffix: Microsoft Intune
description: Permita o acesso a dados da empresa em dispositivos e proteja os dados contra fugas com o Microsoft Intune.
keywords: proteção de dados para impedir fugas em dispositivos com o Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3affffdf69445ced667d718587303a5409423bf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502406"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Impedir fugas de dados em dispositivos não geridos com o Microsoft Intune

Se permitir o acesso a dados da empresa alojados pelo Office 365, pode controlar a forma como os utilizadores partilham e guardam dados sem correr o risco de fugas de dados intencionais ou acidentais. O Microsoft Intune fornece políticas de proteção de aplicações que pode definir para proteger os dados da sua empresa em dispositivos pertencentes ao utilizador. Os dispositivos não precisam de estar inscritos no serviço do Intune. 

As políticas de proteção de aplicações configuradas com o Intune também funcionam em dispositivos geridos com uma solução de gestão de um dispositivo que não seja da Microsoft. Os dados pessoais nos dispositivos não são modificados. Apenas os dados da empresa são geridos pelo departamento de TI. 

Pode definir políticas de proteção de aplicações para as aplicações do Office para dispositivos móveis em dispositivos Windows, iOS ou Android, de forma a proteger os dados da empresa. Estas políticas permitem-lhe definir políticas, por exemplo um PIN com base na aplicação ou encriptação dos dados da empresa, ou definições mais avançadas para restringir a forma como as funcionalidades cortar, copiar, colar e guardar como são utilizadas pelos utilizadores entre aplicações geridas e não geridas. Também pode apagar os dados da empresa remotamente sem a necessidade de os utilizadores inscreverem os dispositivos.

As políticas de proteção de aplicações do Intune são independentes da gestão de dispositivos. As políticas de proteção de aplicações permitem-lhe gerir as aplicações do Office para dispositivos móveis em dispositivos geridos e não geridos pelo Intune, bem como em dispositivos geridos por soluções de MDM que não sejam da Microsoft.

## <a name="before-you-begin"></a>Antes de começar

O plano de ação seguinte pode ser utilizado quando cumprir os seguintes requisitos:

* A sua empresa está pronta para fazer a transição segura para a cloud.
* A sua empresa utiliza o Office 365 Exchange Online, SharePoint Online, OneDrive para Empresas ou Yammer.
* A sua empresa tem licenças do Microsoft 365, Enterprise Mobility + Security (EMS) ou Azure Information Protection.
* A sua empresa permite que os utilizadores acedam a dados da empresa a partir de dispositivos Windows, iOS ou Android pertencentes à empresa ou pessoais.
* A sua empresa não quer exigir que os dispositivos pessoais sejam inscritos num serviço de gestão de dispositivos.

## <a name="action-plan"></a>Plano de ação

Para dispositivos iOS e Android:

1. Saiba como as [políticas de proteção de aplicações](../apps/app-protection-policy.md) funcionam.
2. Saiba como [criar e implementar políticas de proteção de aplicações](../apps/app-protection-policies.md) para as aplicações do Office para dispositivos móveis.
3. [Monitorize as políticas de proteção de aplicações](../apps/app-protection-policies-monitor.md) que cria e implementa.

Para dispositivos Windows 10:

1. Saiba [como o Windows Information Protection (WIP) funciona](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip).
2. Prepare-se para configurar [políticas de proteção de aplicações para o Windows 10](../apps/app-protection-policies-configure-windows-10.md).
3. [Crie e implemente políticas de proteção de aplicações do WIP com o Intune](../apps/windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>O que dizer aos funcionários e estudantes

Consoante aplicável, partilhe as seguintes ligações para fornecer informações adicionais:

* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-ios.md)
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](../fundamentals/end-user-mam-apps-android.md)

## <a name="next-steps"></a>Próximos passos

Precisa de ajuda a ativar este ou outros cenários do Office 365 ou EMS? Se tiver pelo menos 150 licenças do Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilize os seus [benefícios do FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program).
