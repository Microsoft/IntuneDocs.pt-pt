---
title: "Defesa Contra Ameaças para Dispositivos Móveis com o Microsoft Intune"
titleSuffix: 
description: "Utilize a Defesa Contra Ameaças para Dispositivos Móveis (MTD) do Intune em conjunto com o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis para proteger o acesso aos recursos empresariais com base no risco dos dispositivos."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2eaba4f04d6a1daedf40b7b37d2b44ed5aff4533
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/08/2018
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>O que é a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune?


Os conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune permitem-lhe recorrer ao seu fornecedor de Defesa Contra Ameaças para Dispositivos Móveis escolhido como uma fonte de informações sobre as suas políticas de conformidade e regras de acesso condicional. Isto permite aos administradores de TI adicionar uma camada de segurança aos recursos da sua empresa, como o Exchange e o SharePoint, em particular a partir de dispositivos móveis comprometidos.

## <a name="what-problem-does-this-solve"></a>Que problema é que isto resolve?

As empresas precisam de proteger os dados confidenciais de ameaças emergentes que incluem ameaças com base na rede, com base na aplicação e físicas, bem como vulnerabilidades do sistema operativo.

Historicamente, as empresas sempre foram proativas ao proteger os PCs contra ataques, enquanto os dispositivos móveis permanecem não monitorizados e desprotegidos. As plataformas móveis têm proteção incorporada, como o isolamento de aplicações e lojas de aplicações de clientes avaliadas, mas estas plataformas permanecem vulneráveis a ataques sofisticados. Hoje em dia, os funcionários utilizam cada vez mais os dispositivos para trabalhar e precisam de aceder a informações confidenciais. Os dispositivos têm de ser protegidos contra ataques cada vez mais sofisticados.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Como é que os conectores da Defesa Contra Ameaças para Dispositivos Móveis do Intune funcionam?

Os conectores protegem os recursos da empresa ao criar um canal de comunicação entre o Intune e o seu fornecedor de Defesa Contra Ameaças para Dispositivos Móveis escolhido. Os parceiros de Defesa Contra Ameaças Para Dispositivos Móveis do Intune oferecem aplicações intuitivas e fáceis de implementar para dispositivos móveis, que detetam e analisam ativamente as informações sobre ameaças a serem partilhadas com o Intune, quer para efeitos de imposição ou para enviar relatórios. 

Por exemplo, se uma aplicação ligada à Defesa Contra Ameaças para Dispositivos Móveis comunicar ao fornecedor de Defesa Contra Ameaças para Dispositivos Móveis que um certo telemóvel na sua rede está atualmente ligado a uma rede vulnerável a ataques man-in-the-middle, estas informações são partilhadas e categorizadas com o nível de risco adequado (baixo/médio/alto), as quais poderá comparar com as permissões de níveis de risco que configurou no Intune para determinar se o acesso aos recursos que escolher deve ser revogado enquanto o dispositivo estiver comprometido.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Que dados são recolhidos pelo Intune para a Defesa Contra Ameaças para Dispositivos Móveis?

O Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Defesa Contra Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS 11 ou uma versão superior.

**Inventário de aplicações**  
Os inventários de dispositivos iOS pessoais ou empresariais com o iOS 11 ou uma versão superior são enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

 - ID da Aplicação
 - Versão da Aplicação
 - Versão Abreviada da Aplicação
 - Nome da Aplicação
 - Tamanho da Coleção de Pacotes de Aplicação
 - Tamanho Dinâmico da Aplicação
 - A aplicação é ou não validada
 - A aplicação é ou não gerida

## <a name="sample-scenarios"></a>Cenários de exemplo

Quando um dispositivo é considerado infetado pela solução de Defesa Contra Ameaças para Dispositivos Móveis:

![Imagem a mostrar um dispositivo infetado com a Defesa Contra Ameaças para Dispositivos Móveis](./media/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Imagem a mostrar o acesso concedido pela Defesa Contra Ameaças para Dispositivos Móveis](./media/MTD-image-2.png)

> [!NOTE] 
> Não é suportada a utilização de múltiplos fornecedores de Defesa Contra Ameaças para Dispositivos Móveis com o Intune. Ter múltiplas ferramentas MTD ativadas irá forçar a instalação de todas as aplicações MTD, bem como a análise de ameaças entre dispositivos.

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
