---
title: Usar Conformidade de Atualizações relatórios para atualizações do Windows no Microsoft Intune
titleSuffix: Microsoft Intune
description: Use o OMS Conformidade de Atualizações para exibir dados de relatório para atualizações do Windows implantadas com o Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732472"
---
# <a name="intune-compliance-reports-for-updates"></a>Relatórios de conformidade do Intune para atualizações
Quando você usa o Intune para implantar o Windows Update em dispositivos Windows 10, veja detalhes sobre a conformidade da atualização usando o Intune ou uma solução gratuita chamada *conformidade de atualizações*, que faz parte do Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Usar o Intune
Para examinar um relatório de política sobre o status de implantação para os anéis de atualização do Windows 10 que você configurou: 
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

## <a name="use-update-compliance"></a>Usar Conformidade de Atualizações
Você pode monitorar as distribuições de atualização do Windows 10 usando [conformidade de atualizações](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), uma solução de análise do Windows. O Conformidade de Atualizações é oferecido por meio do portal do Azure e está disponível gratuitamente para dispositivos que atendem aos seus [pré-requisitos](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

Ao usar essa solução, você implanta uma ID comercial em qualquer um dos dispositivos Windows 10 gerenciados pelo Intune para os quais deseja relatar a conformidade da atualização.  

No console do Intune, você usa as configurações de OMA-URI de uma política personalizada para configurar a ID comercial. Para obter mais detalhes, veja [Definições de política do Intune para dispositivos com o Windows 10 no Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

O caminho OMA-URI (com distinção entre maiúsculas e minúsculas) para configurar a ID comercial é: *./VENDOR/MSFT/DMCLIENT/Provider/MS DM Server/commercialid*  

Por exemplo, pode utilizar os seguintes valores na **Definição Adicionar ou editar OMA-URI**:
- **Nome da configuração**: ID comercial do Windows Analytics
- **Descrição da configuração**: Configurando a ID comercial para soluções do Windows Analytics
- **OMA-URI** (diferencia maiúsculas de minúsculas): *./Vendor/MSFT/DMClient/Provider/MS DM Server/commercialid*
- **Tipo de dados**: Cadeia
- **Valor**: \<Use o GUID mostrado na guia telemetria do Windows em seu espaço de trabalho do OMS >
 
> [!NOTE]  
> Para obter mais informações sobre o servidor de DM MS, veja [Fornecedor de serviço de configuração (CSP) do DMClient]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Passos seguintes
[Gerenciar atualizações de software no Intune](windows-update-for-business-configure.md)

