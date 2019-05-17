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
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd1dbb3280fbbb93423796b18f6dd85a50a41f11
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59897402"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funcionalidades do método de inscrição do Intune para dispositivos Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Existem vários métodos para inscrever os dispositivos da força de trabalho no Intune. Cada método possui diferentes funcionalidades e melhores práticas, conforme demonstrado nas tabelas abaixo.

## <a name="best-practices-by-enrollment-method"></a>Melhores práticas por método de inscrição
| **Melhores práticas** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Microsoft Azure AD associado ao Autopilot (Modo orientado pelo utilizador)](enrollment-autopilot.md)** |**[Microsoft Azure AD associado ao Autopilot (Modo de implementação automática)](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Utilizados habitualmente no Intune for Education|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Dispositivos que podem ser utilizados como dispositivos partilhados|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Dispositivos pessoais que têm de aceder a recursos da empresa|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Gestão personalizada de aplicações|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funcionalidades por método de inscrição

| **Funcionalidades** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Microsoft Azure AD associado ao Autopilot (Modo orientado pelo utilizador)](enrollment-autopilot.md)** |**[Microsoft Azure AD associado ao Autopilot (Modo de implementação automática)](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Cogestão](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Acesso condicional                                      |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|O utilizador é associado ao dispositivo                    |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Requer o Azure AD Premium                               |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|O dispositivo pode avaliar os recursos protegidos por AC             |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Os utilizadores não podem ser administradores dos respetivos dispositivos               |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidade de configurar a experiência de configuração do dispositivo        |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidade de inscrever dispositivos sem a interação do utilizador      |![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Capacidade de executar scripts do PowerShell                       |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Suporta a inscrição automática após a associação a um domínio do AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD Híbrido|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD       |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Próximos passos

[Configurar a inscrição para dispositivos Windows](windows-enroll.md)

