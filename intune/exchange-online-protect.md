---
title: Exchange sem gestão de dispositivos
titleSuffix: Microsoft Intune
description: Utilize o Microsoft Intune para dar aos funcionários acesso ao respetivo e-mail do Exchange Online do Office 365 sem configurar um sistema de gestão de dispositivos.
keywords: Acesso ao e-mail do Office 365 Exchange
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: archived
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64a872a43a0f8353a6f0e5ad15f4a96d25cf6ef0
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512171"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Proteger o Office 365 Exchange Online sem a necessidade de uma gestão de dispositivos

Se quiser dar aos funcionários acesso ao respetivo e-mail profissional sem os custos de configuração de um sistema de gestão de dispositivos, pode fazê-lo. Pode conceder acesso ao Office 365 Exchange Online através do Intune. Para concluir os passos necessários, confirme se tem licenças para o Microsoft 365 ou Azure Active Directory (premium) e Intune. Os funcionários têm de ter um [dispositivo iOS ou Android suportado](supported-devices-browsers.md). 

Também pode optar por definir um sistema de gestão de dispositivos. Este tipo de proteção de aplicações funciona de forma independente da gestão de dispositivos. 

## <a name="action-plan"></a>Plano de ação

1. [Saiba mais sobre o acesso condicional](conditional-access.md). 
2. [Saiba mais sobre o acesso condicional com base na aplicação](app-based-conditional-access-intune.md).
3. [Definir políticas de acesso condicional com base na aplicação para o Exchange Online](app-based-conditional-access-intune-create.md).
4. [Bloqueie aplicações que não podem ser geridas](app-modern-authentication-block.md), especificamente as aplicações que não utilizam a Azure Active Directory Authentication Library (ADAL).
5. (Opcional) [Configurar políticas de acesso condicional com base na aplicação para o SharePoint Online](app-based-conditional-access-intune-create.md). Estas políticas bloqueiam o acesso aos dados da sua empresa a partir de aplicações que não podem ser geridas e protegidas. As políticas também limitam o acesso através do SharePoint para dispositivos móveis. 

## <a name="what-to-tell-employees-and-students"></a>O que dizer aos funcionários e estudantes

* Peça aos seus funcionários e estudantes para transferirem e instalarem o Microsoft Outlook ou Microsoft SharePoint para iOS a partir da Apple App Store ou para Android a partir da Google Play Store. 
* Se bloquear o acesso a aplicações que não utilizem autenticação moderna, informe os funcionários e estudantes sobre esta restrição. 

## <a name="next-steps"></a>Passos Seguintes

Utilizou o acesso condicional com base na aplicação para aumentar a segurança dos dados da empresa. Como parte dos passos seguintes, pode saber mais sobre outras formas de aumentar a proteção dos dados da sua empresa, incluindo: 

* Configurando [acesso condicional com base na conformidade do dispositivo, risco do dispositivo, localização e atributos do utilizador no Active Directory e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Configurar políticas de proteção de aplicações para o ajudar a proteger os dados da sua empresa contra fugas de dados intencionais e não intencionais. 
* Tirar partido do Azure Information Protection para proteger os dados da empresa fora da sua rede. 

Precisa de ajuda a ativar este ou outros cenários do Office 365 ou EMS? Se tiver pelo menos 150 licenças do Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilize os seus [benefícios do FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
