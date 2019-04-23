---
title: Defesa Contra Ameaças para Dispositivos Móveis com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize a Defesa Contra Ameaças para Dispositivos Móveis (MTD) do Intune em conjunto com o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis para proteger o acesso aos recursos empresariais com base no risco dos dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e364ad88591b8ecc945702659255d9378723624f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513039"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>O que é a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune?
Intune pode integrar dados de um fornecedor de defesa contra ameaças móveis como uma origem de informações para políticas de conformidade e regras de acesso condicional. Pode usar essas informações para ajudar a proteger recursos da empresa, como o Exchange e SharePoint, ao bloquear o acesso a partir de dispositivos móveis comprometidos.  

## <a name="what-problem-does-this-solve"></a>Que problema é que isto resolve?
Integração de informações de um fornecedor de defesa contra ameaças móveis pode ajudar a proteger os recursos da empresa de ameaças que afetam as plataformas móveis.  

Normalmente, as empresas estão proativas em proteger os PCs contra vulnerabilidades e atacam enquanto dispositivos móveis, muitas vezes, não monitorizados e desprotegidos. Em que plataformas móveis terem proteção incorporada, como o isolamento de aplicações e lojas de aplicações de clientes avaliadas, estas plataformas permanecem vulneráveis a ataques sofisticados. Conforme mais funcionários utilizem os dispositivos para trabalhar e aceder a informações confidenciais, as informações do fornecedor de defesa contra ameaças móveis podem ajudar a proteger os dispositivos e seus recursos contra ataques cada vez mais sofisticados.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Como é que os conectores da Defesa Contra Ameaças para Dispositivos Móveis do Intune funcionam?

Para criar um canal de comunicação entre o Intune e o seu fornecedor de defesa contra ameaças móveis escolhido, o Intune utiliza um conector de defesa contra ameaças móveis. Parceiros de defesa contra ameaças do Intune Mobile oferecem intuitivas e fáceis de implementar aplicações para dispositivos móveis. Estas aplicações e analisam ativamente as informações de ameaças para partilhar com o Intune. Intune pode utilizar os dados para fins de relatórios ou imposição.  

Por exemplo: Uma aplicação de Mobile Threat Defense ligada relatórios ao fornecedor de defesa contra ameaças móveis do que um telefone na sua rede está atualmente ligado a uma rede vulnerável a Man nos ataques de meio. Esta informação é categorizada a um nível de risco adequado de baixa, média ou alta. Este nível de risco é, em seguida, em comparação com as permissões de nível de risco que definir no Intune. Com base nesta comparação, acesso a determinados recursos da sua preferência pode ser revogado enquanto o dispositivo estiver comprometido.

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

![Imagem a mostrar um dispositivo infetado com a Defesa Contra Ameaças para Dispositivos Móveis](./media/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Imagem a mostrar o acesso concedido pela Defesa Contra Ameaças para Dispositivos Móveis](./media/MTD-image-2.png)

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
- Sophos (detalhes em breve)
- Wandera (detalhes em breve)
