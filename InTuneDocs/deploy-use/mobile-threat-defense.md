---
title: "Defesa contra ameaças para dispositivos móveis do Intune | Documentos da Microsoft"
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
translationtype: Human Translation
ms.sourcegitcommit: b7ab3041a38bd394195a67690d245d1ad9fd0566
ms.openlocfilehash: fd54a1c94c9a4a279710d6be9f7cfe3b48468cb7
ms.lasthandoff: 03/03/2017


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

![](http://i.imgur.com/kF8tI42.png)

O acesso será concedido quando o dispositivo for remediado:

![](http://i.imgur.com/zG4ZrzX.png)

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)