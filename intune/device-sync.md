---
title: Sincronizar dispositivos com o Intune
titlesuffix: Azure portal
description: "Saiba como sincronizar dispositivos com o Intune para obter as políticas e ações mais recentes."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dadcd33f39827365fc3f22c46d4332f3ea3cbf09
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/23/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronizar dispositivos com o Intune para obter as políticas e ações mais recentes


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A ação **Sincronizar** dispositivo força o dispositivo selecionado a registar-se imediatamente com o Intune. Quando um dispositivo dá entrada, recebe imediatamente todas as ações ou políticas pendentes que foram atribuídas ao mesmo.  Esta ação pode ajudá-lo a validar e resolver imediatamente problemas de políticas que atribuiu, sem esperar pela próxima entrada agendada.

## <a name="supported-platforms"></a>Plataformas suportadas

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="how-to-sync-a-device"></a>Como sincronizar um dispositivo

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.
4. No painel **Dispositivos e grupos**, selecione **Todos os dispositivos**.
5. Na lista de dispositivos que gere, escolha um dispositivo e, em seguida, escolha a ação remota **Sincronizar**.
7. Selecione **Sim** para confirmar a ação.


## <a name="retriable-error-codes"></a>Códigos de erro repetível

Quando um administrador executa a ação de dispositivo **Sincronizar**, as aplicações iOS e Android com falhas que geraram um código de erro repetível estarão disponíveis no dispositivo. No entanto, as aplicações que geraram um código de erro não repetível têm de esperar sete dias antes de poderem estar disponíveis no dispositivo.


| Código de Erro  | Descrição Sugerida                                                                                                                  | Repetível |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 2016330898 | Ocorreu um erro desconhecido.                                                                                                             | Não        |
| 2016330897 | A sua ligação ao Intune excedeu o limite de tempo. Reinicie a sua ligação                                                                             | Sim       |
| 2016330896 | Perdeu a ligação à Internet. Reinicie a sua ligação.                                                                            | Sim       |
| 2016330895 | Perdeu a ligação à Internet. Reinicie a sua ligação.                                                                            | Sim       |
| 2016330894 | Perdeu a ligação à Internet. Reinicie a sua ligação.                                                                            | Sim       |
| 2016330893 | Perdeu a ligação à Internet. Reinicie a sua ligação.                                                                            | Sim       |
| 2016330892 | O roaming internacional está desativado.                                                                                                     | Não        |
| 2016330891 | A ligação de dados via rede móvel para este dispositivo não pode ser acedida durante uma chamada. Aguarde a conclusão da chamada. | Sim       |
| 2016330890 | A rede móvel deste dispositivo. Neste momento, estes dispositivos não podem ser utilizados.                                                   | Não        |
| 2016330889 | A ligação segura falhou. Reinicie a sua ligação.                                                                                   | Sim       |
| 2016330888 | A avaliação da fidedignidade do servidor falhou.                                                                                                | Não        |

## <a name="next-steps"></a>Passos seguintes

Selecione **Ações do Dispositivo** para ver o estado da ação de sincronização. 
