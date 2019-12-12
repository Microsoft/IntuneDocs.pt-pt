---
title: Usar Conformidade de Atualizações relatórios para atualizações do Windows no Microsoft Intune
titleSuffix: Microsoft Intune
description: Use o OMS Conformidade de Atualizações para exibir dados de relatório para atualizações do Windows implantadas com o Intune.
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
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74465719"
---
# <a name="intune-compliance-reports-for-updates"></a>Relatórios de conformidade do Intune para atualizações

Quando você usa o Intune para implantar o Windows Update em dispositivos Windows 10, veja detalhes sobre a conformidade da atualização usando o Intune ou uma solução gratuita chamada *conformidade de atualizações*, que faz parte do Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Usar o Intune

Para examinar um relatório de política sobre o status de implantação para os anéis de atualização do Windows 10 que você configurou:

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **visão geral** > **status de atualização de software**. Poderá ver informações gerais sobre o estado de qualquer cadência de atualizações que tenha atribuído.

3. Para exibir detalhes adicionais, selecione **Monitor**. Em seguida, abaixo **das atualizações de software**, selecione **por estado de implantação de anel de atualização** e escolha o anel de implantação a ser revisado.

   Na secção **Monitorizar**, selecione um dos seguintes relatórios para ver informações mais detalhadas sobre a cadência de atualização:

   - **Status do dispositivo**-isso mostrará o status de configuração do dispositivo, para obter detalhes, consulte [Atualizar deviceConfigurationDeviceStatus]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **Status do usuário**– isso mostrará o nome de usuário, o status e a data do último relatório, para obter detalhes, consulte [list deviceConfigurationUserStatuses](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **Status de atualização do usuário final**– isso mostrará o estado de atualização do dispositivo Windows, para obter detalhes, consulte [windowsUpdateState](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Usar Conformidade de Atualizações

Você pode monitorar as distribuições de atualização do Windows 10 usando [conformidade de atualizações](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), uma solução de análise do Windows. O Conformidade de Atualizações é oferecido por meio do portal do Azure e está disponível gratuitamente para dispositivos que atendem aos seus [pré-requisitos](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Ao usar essa solução, você implanta uma ID comercial em qualquer um dos dispositivos Windows 10 gerenciados pelo Intune para os quais deseja relatar a conformidade da atualização.  

No Intune, você usa as configurações de OMA-URI de uma política personalizada para configurar a ID comercial. Consulte [configurações de política do Intune para dispositivos Windows 10 no Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

O caminho OMA-URI (com distinção entre maiúsculas e minúsculas) para configurar a ID comercial é: *./VENDOR/MSFT/DMCLIENT/Provider/MS DM Server/commercialid*  

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:

- **Nome da Definição**: ID Comercial do Windows Analytics
- **Descrição da Definição**: configurar o ID comercial para soluções do Windows Analytics
- **OMA-URI** (diferencia maiúsculas de minúsculas): *./Vendor/MSFT/DMClient/Provider/MS DM Server/commercialid*
- **Tipo de Dados:** cadeia
- **Valor**: \<use o GUID mostrado na guia telemetria do Windows em seu espaço de trabalho do OMS >

> [!NOTE]
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Próximos passos

[Gerenciar atualizações de software no Intune](windows-update-for-business-configure.md)
