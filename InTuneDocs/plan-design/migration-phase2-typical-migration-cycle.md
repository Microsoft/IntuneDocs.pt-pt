---
title: "Como funciona um ciclo de migração do Intune típico | Documentos da Microsoft"
description: "O objetivo deste artigo é explicar como funciona um ciclo de migração do Intune e dar exemplos sobre como o cliente deve realizar os ciclos de migração."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: aa8fb215772b6e8d3a913d929c030d68e363970b
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-typical-migration-cycle"></a>Fase 2: Ciclo de Migração Típico

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

- Veja [como correu o processo de migração de um fornecedor de MDM de terceiros para o Intune da Adatum Corporation](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Monitorização da migração

O Microsoft Intune proporciona várias formas de monitorização da migração:

1.  Vistas do grupo de utilizadores do Intune

2.  Conjunto de relatórios incorporados e

3.  Alertas na consola.

Deve controlar o número de utilizadores que têm dispositivos inscritos depois de cada fase para poder:

-   Avaliar a eficácia do plano de comunicação.

-   Calcular o impacto da imposição do acesso condicional.

Saiba [como monitorizar uma migração do Intune](https://docs.microsoft.com/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports).

## <a name="post-migration"></a>Pós-migração

Terá de extinguir o fornecedor de MDM anterior e/ou anular a subscrição do serviço após a migração para o Intune. Além disso, terá de remover quaisquer requisitos de infraestrutura desnecessários ao seguir as instruções do fornecedor de MDM.

