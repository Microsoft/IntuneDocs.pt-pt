---
title: Use Update Compliance reports for Windows Updates in Microsoft Intune
titleSuffix: Microsoft Intune
description: Use OMS Update Compliance to view report data for Windows Updates you deploy with Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0de98a0820e15a09c2b3724b216359580327259e
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465719"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune compliance reports for updates

When you use Intune to deploy Windows update to Windows 10 devices, view details about update compliance by using Intune or a free solution called *Update Compliance*, which is part of the Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Use Intune

To review a policy report on the deployment status for the Windows 10 update rings that you have configured:

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Devices** > **Overview** > **Software update status**. Poderá ver informações gerais sobre o estado de qualquer cadência de atualizações que tenha atribuído.

3. To view additional details, select **Monitor**. Then below **Software updates**, select **Per update ring deployment state** and choose the deployment ring to review.

   Na secção **Monitorizar**, selecione um dos seguintes relatórios para ver informações mais detalhadas sobre a cadência de atualização:

   - **Device status**- This will show the device configuration status, for details see [Update deviceConfigurationDeviceStatus]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **User status**- This will show the user name, status, and last report date, for details see [List deviceConfigurationUserStatuses](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **End user update status**- This will show the Windows device update state, for details see [windowsUpdateState](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Use Update Compliance

You can monitor Windows 10 update rollouts by using [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), a Windows Analytics solution. Update Compliance is offered through the Azure portal and is available free for devices that meet its [prerequisites](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

When you use this solution, you deploy a commercial ID to any of your Intune managed Windows 10 devices for which you want to report update compliance.  

In Intune, you use the OMA-URI settings of a custom policy to configure the commercial ID. See [Intune policy settings for Windows 10 devices in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

The OMA-URI (case sensitive) path for configuring the commercial ID is: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:

- **Nome da Definição**: ID Comercial do Windows Analytics
- **Descrição da Definição**: configurar o ID comercial para soluções do Windows Analytics
- **OMA-URI** (case sensitive): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Tipo de Dados:** cadeia
- **Value**: \<Use the GUID shown on the Windows Telemetry tab in your OMS workspace>

> [!NOTE]
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Próximos passos

[Manage software updates in Intune](windows-update-for-business-configure.md)
