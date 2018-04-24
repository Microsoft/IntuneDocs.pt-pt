---
title: Sincronizar dispositivos com o Microsoft Intune – Azure | Microsoft Docs
description: Sincronize dispositivos registados ou geridos com o Microsoft Intune para obter as políticas e ações mais recentes. Inclui os passos para sincronizar através do portal do Azure e lista os códigos de erro que podem ser repetidos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1c098c3d7f71a45830f45877f5ce794d9e112b5e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Sincronizar dispositivos para obter as políticas e ações mais recentes com o Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A ação **Sincronizar** dispositivo força o dispositivo selecionado a registar-se imediatamente com o Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo. Esta funcionalidade pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.

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

## <a name="next-steps"></a>Próximos passos

- Para ver o estado da ação de sincronização, selecione **Ações do dispositivo**. 
