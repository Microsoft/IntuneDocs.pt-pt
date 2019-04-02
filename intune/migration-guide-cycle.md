---
title: Como funciona um ciclo de migração do Intune típico
titleSuffix: Microsoft Intune
description: Este artigo explica como um ciclo de migração do Microsoft Intune funciona e dá-lhe exemplos sobre como processar os ciclos de migração.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3919ae461fbbd5c5c69c1fbe4983cc8468f576c6
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798610"
---
# <a name="typical-migration-cycle"></a>Ciclo de migração típico

É comum uma organização iniciar a migração do Intune com um pequeno piloto ao filtrar um subconjunto dos utilizadores no departamento de TI. Além disso, a sua organização poderá ter de debater fatores como a vontade de mudança do grupo, o número de utilizadores, a complexidade, os requisitos, a localização e o risco comercial para ajudar a determinar o intervalo de tempo da migração.

Veja a seguir um exemplo de como os seus grupos de destino podem ser agendados:

  | **Grupos de destino da migração** | **Período de tempo 1** | **Período de tempo 2** | **Período de tempo 3** | **Período de tempo 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Organização de TI Piloto Limitada (50 utilizadores) | Anunciar o Plano | Dar instrução para a inscrição | Dar um prazo | Impor o acesso condicional |  |                                                        
| Organização de TI Piloto Expandida (200 utilizadores) |  | Anunciar o Plano | Dar instrução para a inscrição | Dar um prazo | Impor o acesso condicional |
| Fase 1 da migração Utilizadores com grandes conhecimentos de tecnologia (2000) |  |  | Anunciar o Plano | Dar instrução para a inscrição | Dar um prazo |
| Fase 2 da migração Leste dos EUA |  |  |  | Anunciar o Plano | Dar instrução para a inscrição |
| Todas as Regiões |  |  |  |  | Anunciar o Plano |

## <a name="customer-migration-case-study"></a>Caso prático da migração do cliente

### <a name="adatum-corporation"></a>Adatum Corporation

Veja [como correu o processo de migração de um fornecedor de MDM de terceiros para o Intune da Adatum Corporation](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Monitorização da migração

O Intune proporciona várias formas de monitorização da migração:

* Vistas do grupo de utilizadores do Intune

* Conjunto de relatórios incorporados

* Alertas na consola

Controle o número de utilizadores que têm dispositivos inscritos depois de cada fase para poder:

-   Avaliar a eficácia do plano de comunicação.

-   Calcular o impacto da imposição do acesso condicional.


## <a name="post-migration"></a>Pós-migração

Extinga o fornecedor de MDM anterior e anule a subscrição do serviço após a migração para o Intune. Além disso, remova todos os requisitos de infraestrutura desnecessários ao seguir as instruções do fornecedor de MDM.
