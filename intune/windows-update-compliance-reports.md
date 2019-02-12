---
title: Utilize os relatórios de conformidade de atualização para atualizações do Windows no Microsoft Intune | Documentos da Microsoft
description: Utilize a conformidade de atualizações do OMS para ver dados do relatório de atualizações do Windows implementou com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa549e90e9c0066ae10772728f097b5951284959
ms.sourcegitcommit: e262b0ad8df610e25eb9421b9ebc2673bcf1020e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/11/2019
ms.locfileid: "55986959"
---
# <a name="intune-compliance-reports-for-updates"></a>Relatórios de conformidade do Intune para atualizações
Ao utilizar o Intune para implementar a atualização do Windows para dispositivos Windows 10, veja os detalhes sobre a conformidade de atualização com o Intune ou uma solução gratuita chamada *compatibilidade da atualização*, que faz parte do Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Utilizar o Intune
Para rever um relatório de política sobre o estado de implementação para as cadências de atualização do Windows 10 que tenha configurado: 
1. Inicie sessão no [portal do Azure](https://portal.azure.com/).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Atualizações de software** > **Descrição Geral**. Poderá ver informações gerais sobre o estado de qualquer cadência de atualizações que tenha atribuído.
4. Abra um dos seguintes relatórios:  

   **Para todas as cadências de implementação**:
   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**
   2. Na secção **Monitorizar**, selecione **Por estado de implementação da cadência de atualização**.  

   **Para cadências de implementação específicas**:  

   1. Em **Atualizações de software** > **Cadências de Atualização do Windows 10**, selecione a cadência de implementação a analisar.  
   2. Na secção **Monitorizar**, selecione um dos seguintes relatórios para ver informações mais detalhadas sobre a cadência de atualização:  
      - **Estado do dispositivo**  
      - **Estado de utilizador**  

## <a name="use-update-compliance"></a>Utilize a conformidade de atualização
Pode monitorizar implementações de atualizações do Windows 10 através de [compatibilidade da atualização](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), uma solução de análise do Windows. Conformidade de atualização é disponibilizada através do portal do Azure e está disponível gratuitamente para dispositivos que cumprem a sua [pré-requisitos](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Quando utilizar esta solução, implemente um ID comercial para qualquer um dos seus Intune geridos os dispositivos Windows 10 para o qual pretende reportar a conformidade de atualização.  

Na consola do Intune, utilizar as definições de OMA-URI de uma política personalizada para configurar o ID comercial. Para obter mais detalhes, veja [Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

O caminho do OMA-URI (sensível a maiúsculas e minúsculas) para configurar o ID comercial é: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:
- **Nome da definição**: ID comercial do Windows Analytics
- **Descrição da definição**: Configurar soluções comerciais de ID para o Windows Analytics
- **OMA-URI** (sensível a maiúsculas e minúsculas): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Tipo de dados**: Cadeia
- **Valor**: \<Utilizar o GUID apresentado no separador telemetria do Windows na sua área de trabalho do OMS >
 
> [!NOTE]  
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Passos Seguintes
[Gerir atualizações de software no Intune](windows-update-for-business-configure.md)

