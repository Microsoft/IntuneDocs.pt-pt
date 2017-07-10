---
title: "Defesa contra ameaças para dispositivos móveis do Intune"
description: Proteja o acesso aos recursos da empresa com base no risco do dispositivo.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85f3ed28b021c0aa2b00f128297eb0d99cf0bc1c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="intune-mobile-threat-defense-connectors"></a>Conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Os conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune permitem-lhe recorrer ao seu fornecedor de Defesa Contra Ameaças para Dispositivos Móveis escolhido como uma fonte de informações sobre as suas políticas de conformidade e regras de acesso condicional. Isto permite aos Administradores de TI adicionar uma camada de segurança aos recursos da sua empresa, como o Exchange e o SharePoint, em particular a partir de dispositivos móveis comprometidos.

## <a name="what-problem-does-this-solve"></a>Que problema é que isto resolve?

As empresas precisam de proteger os dados confidenciais de ameaças emergentes que incluem ameaças com base na rede, com base na aplicação e físicas, bem como vulnerabilidades do sistema operativo.
No passado, as empresas sempre foram proativas ao proteger os PCs contra ataques, enquanto os dispositivos móveis permaneciam não monitorizados e desprotegidos. As plataformas móveis têm proteção incorporada, como o isolamento de aplicações e lojas de aplicações de clientes avaliadas, mas estas plataformas permanecem vulneráveis a ataques sofisticados. Hoje em dia, os funcionários utilizam cada vez mais os dispositivos para trabalhar e precisam de aceder a informações confidenciais. Os dispositivos têm de ser protegidos contra ataques cada vez mais sofisticados.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Como funcionam os conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune?

Os conectores protegem os recursos da empresa ao criar um canal de comunicação entre o Intune e o seu fornecedor de Defesa Contra Ameaças para Dispositivos Móveis escolhido. Os parceiros de Defesa Contra Ameaças Para Dispositivos Móveis do Intune oferecem aplicações intuitivas e fáceis de implementar para dispositivos móveis, que detetam e analisam ativamente as informações sobre ameaças a serem partilhadas com o Intune, quer para efeitos de imposição ou para enviar relatórios. Por exemplo, se uma aplicação ligada à Defesa Contra Ameaças para Dispositivos Móveis comunicar ao fornecedor de Defesa Contra Ameaças para Dispositivos Móveis que um certo telemóvel na sua rede está atualmente ligado a uma rede vulnerável a ataques man-in-the-middle, estas informações são partilhadas e categorizadas com o nível de risco adequado (baixo/médio/alto), as quais poderá comparar com as permissões de níveis de risco que configurou no Intune para determinar se o acesso aos recursos que escolher deve ser revogado enquanto o dispositivo estiver comprometido.

## <a name="sample-scenarios"></a>Cenários de exemplo

Quando um dispositivo é considerado infetado pela solução de Defesa Contra Ameaças para Dispositivos Móveis:

![Dispositivo considerado infetado pela Defesa Contra Ameaças para Dispositivos Móveis](../media/mtp/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Acesso à Defesa Contra Ameaças para Dispositivos Móveis concedido](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)
