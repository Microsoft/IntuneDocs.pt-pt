---
title: Defesa Contra Ameaças para Dispositivos Móveis com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize a Defesa Contra Ameaças para Dispositivos Móveis (MTD) do Intune em conjunto com o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis para proteger o acesso aos recursos empresariais com base no risco dos dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97efe5c2445263bba11ee083e89d36fde1986dc1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732396"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>O que é a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune?
O Intune pode integrar dados de um fornecedor de defesa contra ameaças móveis como uma fonte de informações para políticas de conformidade e regras de acesso condicional. Você pode usar essas informações para ajudar a proteger recursos corporativos, como o Exchange e o SharePoint, bloqueando o acesso de dispositivos móveis comprometidos.  

## <a name="what-problem-does-this-solve"></a>Que problema é que isto resolve?
A integração de informações de um fornecedor de defesa contra ameaças móveis pode ajudá-lo a proteger seus recursos corporativos contra ameaças que afetam as plataformas móveis.  

Normalmente, as empresas são proativas na proteção de PCs contra vulnerabilidades e ataques, enquanto os dispositivos móveis geralmente ficam sem monitoramento e desprotegido. Onde as plataformas móveis têm proteção interna, como isolamento de aplicativo e lojas de aplicativos de consumidor verificados, essas plataformas permanecem vulneráveis a ataques sofisticados. À medida que mais funcionários usam dispositivos para o trabalho e acessam informações confidenciais, as informações do fornecedor de defesa contra ameaças móveis podem ajudá-lo a proteger dispositivos e seus recursos contra ataques cada vez mais sofisticados.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Como é que os conectores da Defesa Contra Ameaças para Dispositivos Móveis do Intune funcionam?

O Intune usa um conector de defesa contra ameaças móveis para criar um canal de comunicação entre o Intune e seu fornecedor de defesa contra ameaças móveis escolhido. Os parceiros de defesa contra ameaças móveis do Intune oferecem aplicativos intuitivos e fáceis de implantar para dispositivos móveis. Esses aplicativos examinam e analisam ativamente as informações de ameaças para compartilhar com o Intune. O Intune pode usar os dados para fins de relatório ou imposição.  

Por exemplo: Um aplicativo de defesa contra ameaças móveis conecta-se ao fornecedor de defesa contra ameaças móveis que um telefone em sua rede está conectado atualmente a uma rede que está vulnerável a ataques de interceptação. Essas informações são categorizadas para um nível de risco apropriado de baixo, médio ou alto. Esse nível de risco é comparado com as concessões de nível de risco definidas no Intune. Com base nessa comparação, o acesso a determinados recursos de sua escolha pode ser revogado enquanto o dispositivo é comprometido.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Que dados são recolhidos pelo Intune para a Defesa Contra Ameaças para Dispositivos Móveis?

Se estiver ativado, o Intune recolhe informações do inventário de aplicações de dispositivos pessoais e empresariais e disponibiliza-as aos fornecedores de Defesa Contra Ameaças para Dispositivos Móveis (MTD), como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS.

Este serviço é de participação ativa. Por predefinição, não são partilhadas informações do inventário de aplicações. Um administrador do Intune tem de ativar a Sincronização de Aplicações para dispositivos iOS nas definições do serviço antes de serem partilhadas informações do inventário de aplicações.

**Inventário de aplicações**  
Se ativar a Sincronização de Aplicações para dispositivos iOS, os inventários dos dispositivos iOS pessoais e empresariais serão enviados para o seu fornecedor de serviços de MTD. Os dados no inventário de aplicações incluem:

- ID da Aplicação
- Versão da Aplicação
- Versão Abreviada da Aplicação
- Nome da Aplicação
- Tamanho da Coleção de Pacotes de Aplicação
- Tamanho Dinâmico da Aplicação
- Se a aplicação é ou não validada
- Se a aplicação é ou não gerida

## <a name="sample-scenarios"></a>Cenários de exemplo

Quando um dispositivo é considerado infetado pela solução de Defesa Contra Ameaças para Dispositivos Móveis:

![Imagem a mostrar um dispositivo infetado com a Defesa Contra Ameaças para Dispositivos Móveis](./media/mobile-threat-defense/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Imagem a mostrar o acesso concedido pela Defesa Contra Ameaças para Dispositivos Móveis](./media/mobile-threat-defense/MTD-image-2.png)

> [!NOTE] 
> Não é suportada a utilização de múltiplos fornecedores de Defesa Contra Ameaças para Dispositivos Móveis com o Intune. Ter múltiplas ferramentas MTD ativadas irá forçar a instalação de todas as aplicações MTD, bem como a análise de ameaças entre dispositivos.

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Defesa contra ameaças móveis da vagara](wandera-mtd-connector.md)
