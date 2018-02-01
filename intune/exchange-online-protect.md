---
title: "Proteger o Office 365 Exchange Online sem a necessidade de uma gestão de dispositivos"
description: "Dê aos funcionários acesso ao respetivo e-mail profissional. Não é necessária a gestão do dispositivo."
keywords: Acesso ao e-mail do Office 365 Exchange
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 53872921bc4c7a52224741ab3b743a1d9ac52f42
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Proteger o Office 365 Exchange Online sem a necessidade de uma gestão de dispositivos

Se quiser dar aos funcionários acesso ao respetivo e-mail profissional sem os custos de configuração de um sistema de gestão de dispositivos, pode fazê-lo. Pode conceder acesso ao Office 365 Exchange Online através do Intune. Para concluir os passos necessários, confirme se tem licenças para o Microsoft 365 ou Azure Active Directory (premium) e Intune. Os funcionários têm de ter um [dispositivo iOS ou Android suportado](supported-devices-browsers.md). 

Também pode optar por definir um sistema de gestão de dispositivos. Este tipo de proteção de aplicações funciona de forma independente da gestão de dispositivos. 

## <a name="action-plan"></a>Plano de ação

1. [Saiba mais sobre o acesso condicional](conditional-access.md). 
2. [Saiba mais sobre o acesso condicional com base nas aplicações](app-based-conditional-access-intune.md).
3. [Defina políticas de acesso condicional com base nas aplicações para Exchange Online](app-based-conditional-access-intune-create.md).
4. [Bloqueie aplicações que não podem ser geridas](app-modern-authentication-block.md), especificamente as aplicações que não utilizam a Azure Active Directory Authentication Library (ADAL).
5. (Opcional) [Definir políticas de acesso condicional com base nas aplicações para o SharePoint Online](app-based-conditional-access-intune-create.md). Estas políticas bloqueiam o acesso aos dados da sua empresa a partir de aplicações que não podem ser geridas e protegidas. As políticas também limitam o acesso através do SharePoint para dispositivos móveis. 

## <a name="what-to-tell-employees-and-students"></a>O que dizer aos funcionários e estudantes

* Peça aos seus funcionários e estudantes para transferirem e instalarem o Microsoft Outlook ou Microsoft SharePoint para iOS a partir da Apple App Store ou para Android a partir da Google Play Store. 
* Se bloquear o acesso a aplicações que não utilizem autenticação moderna, informe os funcionários e estudantes sobre esta restrição. 

## <a name="next-steps"></a>Próximos passos

Utilizou o acesso condicional com base nas aplicações para aumentar a segurança dos dados da empresa. Como parte dos passos seguintes, pode saber mais sobre outras formas de aumentar a proteção dos dados da sua empresa, incluindo: 

* Configurar o [acesso condicional com base na conformidade do dispositivo, no risco do dispositivo, na localização e nos atributos de utilizador no Active Directory e Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Configurar políticas de proteção de aplicações para o ajudar a proteger os dados da sua empresa contra fugas de dados intencionais e não intencionais. 
* Tirar partido do Azure Information Protection para proteger os dados da empresa fora da sua rede. 

Precisa de ajuda a ativar este ou outros cenários do Office 365 ou EMS? Se tiver pelo menos 150 licenças do Microsoft 365, Enterprise Mobility + Security ou Azure Active Directory Premium, utilize os seus [benefícios do FastTrack](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 