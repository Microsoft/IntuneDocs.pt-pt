---
title: "Defesa Contra Ameaças a Dispositivos Móveis com o Intune"
titleSuffix: Azure portal
description: Proteger o acesso aos recursos da empresa com base no risco do dispositivo
keywords: 
author: andredm7
ms.author: andredm
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
ms.openlocfilehash: f1d5957acde86b3621009e5c38df42bc894a413c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/25/2018
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integração da Defesa Contra Ameaças a Dispositivos Móveis com o Intune


Os conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune permitem-lhe recorrer ao seu fornecedor de Defesa Contra Ameaças para Dispositivos Móveis escolhido como uma fonte de informações sobre as suas políticas de conformidade e regras de acesso condicional. Isto permite aos administradores de TI adicionar uma camada de segurança aos recursos da sua empresa, como o Exchange e o SharePoint, em particular a partir de dispositivos móveis comprometidos.

## <a name="what-problem-does-this-solve"></a>Que problema é que isto resolve?

As empresas precisam de proteger os dados confidenciais de ameaças emergentes que incluem ameaças com base na rede, com base na aplicação e físicas, bem como vulnerabilidades do sistema operativo.

No passado, as empresas sempre foram proativas ao proteger os PCs contra ataques, enquanto os dispositivos móveis permaneciam não monitorizados e desprotegidos. As plataformas móveis têm proteção incorporada, como o isolamento de aplicações e lojas de aplicações de clientes avaliadas, mas estas plataformas permanecem vulneráveis a ataques sofisticados. Hoje em dia, os funcionários utilizam cada vez mais os dispositivos para trabalhar e precisam de aceder a informações confidenciais. Os dispositivos têm de ser protegidos contra ataques cada vez mais sofisticados.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Como funcionam os conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune?

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

![Dispositivo considerado infetado pela Defesa Contra Ameaças para Dispositivos Móveis](./media/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Acesso à Defesa Contra Ameaças para Dispositivos Móveis concedido](./media/MTD-image-2.png)

> [!NOTE] 
> Não é suportada a utilização de múltiplos fornecedores de Defesa Contra Ameaças para Dispositivos Móveis com o Intune. Ter múltiplas ferramentas MTD ativadas irá forçar a instalação de todas as aplicações MTD, bem como a análise de ameaças entre dispositivos.

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
