---
title: Sincronizar dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Sincronize dispositivos registados ou geridos com o Microsoft Intune para obter as políticas e ações mais recentes. Inclui os passos para sincronizar através do portal do Azure e lista os códigos de erro que podem ser repetidos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f13e00abad5b48dcd7996cf9df1cc5756f250d3
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57388101"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Sincronizar dispositivos para obter as políticas e ações mais recentes com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação **Sincronizar** dispositivo força o dispositivo selecionado a registar-se imediatamente com o Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo. Esta funcionalidade pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Sincronizar um dispositivo

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e, em seguida, selecione **Microsoft Intune**. 
3. No **Intune**, selecione **Dispositivos** > **Todos os dispositivos**.
4. Na lista de dispositivos que gere, selecione um dispositivo, selecione **Mais** e, em seguida, selecione **Sincronizar**.
5. Para confirmar, selecione **Sim**.

Para ver o estado da ação de sincronização, selecione **Dispositivos** > **Ações de dispositivos**.

Pode encontrar padrão Intune política entrada frequências no [tempos de ciclo de atualização](device-profiles.md).

## <a name="retryable-error-codes"></a>Códigos de erro repetíveis

Quando um administrador executa a ação de dispositivo **Sincronizar**, as aplicações iOS e Android com falhas e que geraram um código de erro repetível continuam disponíveis no dispositivo. No entanto, as aplicações que geraram um código de erro não repetível têm de aguardar sete dias antes de estarem disponíveis no dispositivo.


| Código de erro  | Descrição sugerida | Repetível |
|---|---|---|
| 2016330898 | Ocorreu um erro desconhecido. | Não |
| 2016330897 | A sua ligação ao Intune excedeu o limite de tempo. Reinicie a sua ligação. | Sim |
| 2016330896 | Perdeu a ligação à Internet. Reinicie a sua ligação. | Sim |
| 2016330895 | Perdeu a ligação à Internet. Reinicie a sua ligação. | Sim |
| 2016330894 | Perdeu a ligação à Internet. Reinicie a sua ligação. | Sim |
| 2016330893 | Perdeu a ligação à Internet. Reinicie a sua ligação. | Sim|
| 2016330892 | O roaming internacional está desativado. | Não|
| 2016330891 | A ligação de dados via rede móvel para este dispositivo não pode ser acedida durante uma chamada. Aguarde a conclusão da chamada. | Sim|
| 2016330890 | A rede móvel deste dispositivo. Neste momento, estes dispositivos não podem ser utilizados. | Não|
| 2016330889 | A ligação segura falhou. Reinicie a sua ligação. | Sim|
| 2016330888 | A avaliação da fidedignidade do servidor falhou. | Não|

## <a name="next-steps"></a>Passos Seguintes

Pode [verificar os detalhes](device-inventory.md) do dispositivo.
 
