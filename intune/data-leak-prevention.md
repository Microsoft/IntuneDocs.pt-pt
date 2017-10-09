---
title: "Impedir fugas de dados em dispositivos não geridos"
description: Permita o acesso a dados da empresa em dispositivos e proteja os dados contra fugas.
keywords: "proteção de dados para impedir fugas em dispositivos com o Office 365"
author: arob98
manager: angrobe
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ae8702c51df1c3c2b8e6dd2a79bf4599e6b7677
ms.sourcegitcommit: 29ee35da2864b25f4432d2423b285014c77040af
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/23/2017
---
# <a name="prevent-data-leaks-on-non-managed-devices"></a>Impedir fugas de dados em dispositivos não geridos

Se permitir o acesso a dados da empresa alojados pelo Office 365, pode controlar a forma como os utilizadores partilham e guardam dados sem correr o risco de fugas de dados intencionais ou acidentais. O Microsoft Intune fornece políticas de proteção de aplicações que pode definir para proteger os dados da sua empresa em dispositivos pertencentes ao utilizador. Os dispositivos não precisam de estar inscritos no serviço do Intune. 

As políticas de proteção de aplicações configuradas com o Intune também funcionam em dispositivos geridos com uma solução de gestão de um dispositivo que não seja da Microsoft. Os dados pessoais nos dispositivos não são modificados. Apenas os dados da empresa são geridos pelo departamento de TI. 

Pode definir políticas de proteção de aplicações para as aplicações do Office para dispositivos móveis em dispositivos Windows, iOS ou Android, de forma a proteger os dados da empresa. Estas políticas permitem-lhe definir políticas, por exemplo um PIN com base na aplicação ou encriptação dos dados da empresa, ou definições mais avançadas para restringir a forma como as funcionalidades cortar, copiar, colar e guardar como são utilizadas pelos utilizadores entre aplicações geridas e não geridas. Também pode apagar os dados da empresa remotamente sem a necessidade de os utilizadores inscreverem os dispositivos. 

As políticas de proteção de aplicações do Intune são independentes da gestão de dispositivos. As políticas de proteção de aplicações permitem-lhe gerir as aplicações do Office para dispositivos móveis em dispositivos geridos e não geridos pelo Intune, bem como em dispositivos geridos por soluções de MDM que não sejam da Microsoft. 

## <a name="before-you-begin"></a>Antes de começar

O seguinte plano de ação pode ser utilizado se cumprir estes requisitos:
* A sua empresa está pronta para fazer a transição segura para a cloud.
* A sua empresa utiliza o Office 365, Exchange Online, SharePoint Online, OneDrive para Empresas ou Yammer.
* A sua empresa tem licenças do Microsoft 365, Enterprise Mobility + Security (EMS) ou Azure Information Protection.
* A sua empresa permite que os utilizadores acedam a dados da empresa a partir de dispositivos Windows, iOS ou Android pertencentes à empresa ou pessoais. 
* A sua empresa não quer exigir que os dispositivos pessoais sejam inscritos num serviço de gestão de dispositivos. 

## <a name="action-plan"></a>Plano de ação

Para dispositivos iOS e Android: 

1. Saiba como as [políticas de proteção de aplicações](app-protection-policy.md) funcionam.
2. Saiba como [criar e implementar políticas de proteção de aplicações](app-protection-policies.md) para as aplicações do Office para dispositivos móveis. 
3. [Monitorize as políticas de proteção de aplicações](app-protection-policies-monitor.md) que cria e implementa. 

Para dispositivos Windows 10: 

1. Saiba [como o Windows Information Protection (WIP) funciona](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip). 
2. Prepare-se para configurar [políticas de proteção de aplicações para o Windows 10](app-protection-policies-configure-windows-10.md).
3. [Crie e implemente políticas de proteção de aplicações do WIP com o Intune](windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>O que dizer aos funcionários e estudantes

Consoante aplicável, partilhe as seguintes ligações para fornecer informações adicionais: 
* [O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)
* [O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-android.md) 

## <a name="next-steps"></a>Próximos passos

Precisa de ajuda a ativar este ou outros cenários do Office 365 ou EMS? Se tiver pelo menos 150 licenças do Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilize os seus [benefícios do FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 