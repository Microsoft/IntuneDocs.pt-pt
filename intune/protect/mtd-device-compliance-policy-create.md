---
title: Criar uma política de conformidade de dispositivos MTD com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Crie uma política de conformidade de dispositivo do Intune que utilize os níveis de ameaça de parceiro MTD para determinar se um dispositivo móvel pode aceder a recursos da empresa.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409703"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Criar a política de conformidade de dispositivos da Defesa Contra Ameaças para Dispositivos Móveis (MTD) com o Intune

O Intune com a MTD ajuda-o a detetar ameaças e a avaliar os riscos em dispositivos móveis. Pode criar uma regra de política de conformidade de dispositivos do Intune que avalie o risco para determinar se o dispositivo está ou não em conformidade. You can then use a [Conditional Access policy](create-conditional-access-intune.md) to block access to services based on device compliance.

> [!NOTE]
> Estas informações aplicam-se a todos os parceiros de Defesa Contra Ameaças para Dispositivos Móveis.

## <a name="before-you-begin"></a>Antes de começar

Como parte da configuração da MTD, na consola do parceiro MTD, criou uma política que classifica as várias ameaças como sendo de nível alto, médio e baixo. Na política de conformidade de dispositivos do Intune, precisa agora de definir o nível de Defesa Contra Ameaças para Dispositivos Móveis.

Pré-requisitos da política de conformidade de dispositivos com a MTD:

- Configurar a integração da MTD com o Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>Para criar uma política de conformidade MTD do dispositivo

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Device** > **Compliance policies** > **Create policy**.

3. Specify a device compliance policy **Name**, **Description**, select the **Platform**, then select **Configure** under the **Settings** section.

4. No painel **política de conformidade**, selecione **Estado de Funcionamento do Dispositivo**.

5. On the **Device Health** pane, choose the Mobile Threat Level from the drop-down list for **Require the device to be at or under the Device Threat Level**.

   - **Seguro**: este é o nível mais seguro. O dispositivo não pode aceder aos recursos da empresa se contiver ameaças. Se forem detetadas ameaças, o dispositivo será avaliado como não conforme.

   - **Baixo**: o dispositivo está em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.

   - **Médio**: o dispositivo está em conformidade se as ameaças encontradas forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto, o estado do dispositivo será determinado como não conforme.

   - **Elevado**: este é o nível menos seguro. Este nível permite que todos os níveis de ameaça estejam presentes e utiliza a Defesa Contra Ameaças para Dispositivos Móveis apenas para a criação de relatórios. É necessário que os dispositivos tenham a aplicação de MTD ativada com esta definição.

6. Select **OK** twice, then select **Create** to create the policy.

> [!IMPORTANT]
> If you create Conditional Access policies for Office 365 or other services, the device compliance evaluation is assessed and noncompliant devices are blocked from accessing corporate resources until the threat is resolved in the device.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>Para atribuir uma política de conformidade MTD do dispositivo

To assign a device compliance policy to users:

1. Sign in to the [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Select **Device** > **Compliance policies**.

3. Select the policy you want to assign to users, and then select **Assignments**. Use the available options to *Include* and *Exclude* groups to receive this policy.  

4. Select Save to complete the assignment. When you save the assignment, the policy deploys to your selected users and their devices are evaluated for compliance.

## <a name="next-steps"></a>Próximos passos

[Ativar a Defesa Contra Ameaças para Dispositivos Móveis no Intune](mtd-connector-enable.md)
