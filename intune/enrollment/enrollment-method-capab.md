---
title: Funcionalidades do método de inscrição do Intune para dispositivos Windows
titleSuffix: Microsoft Intune
description: Funcionalidades de cada método de inscrição para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6b12bb0066c37eb470065a169a3ad7866c69a17
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503260"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funcionalidades do método de inscrição do Intune para dispositivos Windows
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Existem vários métodos para inscrever os dispositivos da força de trabalho no Intune. Cada método possui diferentes funcionalidades e melhores práticas, conforme demonstrado nas tabelas abaixo.

## <a name="best-practices-by-enrollment-method"></a>Melhores práticas por método de inscrição
| **Melhores práticas** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Microsoft Azure AD associado ao Autopilot (Modo orientado pelo utilizador)](enrollment-autopilot.md)** |**[Microsoft Azure AD associado ao Autopilot (Modo de implementação automática)](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Utilizados habitualmente no Intune for Education|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Dispositivos que podem ser utilizados como dispositivos partilhados|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Dispositivos pessoais que têm de aceder a recursos da empresa|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Gestão personalizada de aplicações|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funcionalidades por método de inscrição

| **Funcionalidades** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Microsoft Azure AD associado ao Autopilot (Modo orientado pelo utilizador)](enrollment-autopilot.md)** |**[Microsoft Azure AD associado ao Autopilot (Modo de implementação automática)](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Conditional Access                                      |![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|O utilizador é associado ao dispositivo                    |![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|Requer o Azure AD Premium                               |![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|O dispositivo pode avaliar os recursos protegidos por AC             |![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|Os utilizadores não podem ser administradores dos respetivos dispositivos               |![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Capacidade de configurar a experiência de configuração do dispositivo        |![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Capacidade de inscrever dispositivos sem a interação do utilizador      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|Capacidade de executar scripts do PowerShell                       |![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|Suporta a inscrição automática após a associação a um domínio do AD      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD Híbrido|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD       |![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![Marca de verificação](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

as cargas de trabalho de aplicativos cliente \* no Configuration Manager devem ser movidas para o Intune Pilot ou o Intune.

## <a name="next-steps"></a>Próximos passos

[Configurar o registro para Windows](windows-enroll.md)

