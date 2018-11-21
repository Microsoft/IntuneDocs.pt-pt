---
title: Funcionalidades do Intune por método de inscrição para dispositivos Windows
titlesuffix: Microsoft Intune
description: Veja as funcionalidades suportadas por cada método de inscrição para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 38bb88015261aa50d6c27aec026614f1205aebe8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189814"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Funcionalidades por método de inscrição para dispositivos Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune permite-lhe gerir os dispositivos e as aplicações da sua força de trabalho e a forma como acedem aos dados da empresa. Os dispositivos têm de ser inscritos primeiro no serviço do Intune. Existem vários métodos para inscrever os dispositivos da força de trabalho. Cada método possui diferentes funcionalidades e melhores práticas, conforme demonstrado nas tabelas abaixo.

## <a name="best-practices-by-enrollment-method"></a>Melhores práticas por método de inscrição
| **Melhores práticas** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD associado ao Autopilot](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Utilizados habitualmente no Intune for Education|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Dispositivos que podem ser utilizados como dispositivos partilhados|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Dispositivos pessoais que têm de aceder a recursos da empresa|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|
|Gestão personalizada de aplicações|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funcionalidades por método de inscrição

| **Funcionalidades** | **[Azure AD associado](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD associado ao Autopilot](enrollment-autopilot.md)** |**[Em massa](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Acesso condicional                                      |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|O utilizador é associado ao dispositivo                    |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Requer o Azure AD Premium                               |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|
|O dispositivo pode avaliar os recursos protegidos por AC             |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|
|Os utilizadores não podem ser administradores dos respetivos dispositivos               |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidade de configurar a experiência de configuração do dispositivo        |![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Capacidade de inscrever dispositivos sem a interação do utilizador      |![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|
|Capacidade de executar scripts do PowerShell                       |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Suporta a inscrição automática após a associação a um domínio do AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD Híbrido|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Marca de verificação](media/checkmark.png)|
|Suporta a inscrição automática após a associação a um domínio do Azure AD       |![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![Marca de verificação](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Passos Seguintes

[Configurar a inscrição para Windows ](windows-enroll.md)

