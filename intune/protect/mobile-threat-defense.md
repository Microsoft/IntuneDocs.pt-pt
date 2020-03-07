---
title: Defesa Contra Ameaças para Dispositivos Móveis com o Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilize a Defesa Contra Ameaças para Dispositivos Móveis (MTD) do Intune em conjunto com o seu parceiro de Defesa Contra Ameaças para Dispositivos Móveis para proteger o acesso aos recursos empresariais com base no risco dos dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f056f665ebee0d1e2315129a4fe739b2c490ca98
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78369501"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integração da Defesa Contra Ameaças a Dispositivos Móveis com o Intune

Intune pode integrar dados de um fornecedor de Defesa de Ameaças Móveis (MTD) como fonte de informação para as políticas de conformidade do dispositivo e regras de acesso condicional do dispositivo. Pode utilizar estas informações para ajudar a proteger recursos corporativos como o Exchange e o SharePoint, bloqueando o acesso a dispositivos móveis comprometidos.

A Intune pode utilizar estes mesmos dados como fonte para dispositivos não matriculados utilizando políticas de proteção de aplicações Intune. Como tal, os administradores podem usar estas informações para ajudar a proteger os dados corporativos dentro de uma [aplicação protegida](~/apps/apps-supported-intune-apps.md)microsoft Intune , e emitir um bloco ou limpeza seletiva.

## <a name="protect-corporate-resources"></a>Proteger os recursos corporativos

A integração de informações dos fornecedores do MTD pode ajudá-lo a proteger os seus recursos corporativos de ameaças que afetam as plataformas móveis.  

Normalmente, as empresas são pró-ativas na proteção dos Computadores contra vulnerabilidades e ataques, enquanto os dispositivos móveis muitas vezes ficam descontrolados e desprotegidos. Onde as plataformas móveis têm proteção incorporada, como o isolamento de aplicações e as lojas de aplicações de consumo vetadas, estas plataformas permanecem vulneráveis a ataques sofisticados. À medida que mais funcionários usam dispositivos para o trabalho e para aceder a informações sensíveis, a informação dos fornecedores do MTD pode ajudá-lo a proteger os dispositivos e os seus recursos de ataques cada vez mais sofisticados.

## <a name="intune-mobile-threat-defense-connectors"></a>Conectores de Defesa Contra Ameaças para Dispositivos Móveis do Intune

Intune usa um conector de defesa de ameaças móveis para criar um canal de comunicação entre Intune e o seu fornecedor MTD escolhido. Os parceiros Intune MTD oferecem aplicações intuitivas e fáceis de implementar para dispositivos móveis. Estas aplicações digitalizam e analisam ativamente informações de ameaças para partilhar com o Intune. A Intune pode utilizar os dados para efeitos de reporte ou de execução.

Por exemplo: Uma aplicação MTD conectada reporta ao fornecedor MTD que um telefone da sua rede está atualmente ligado a uma rede que é vulnerável a ataques Man-in-the-Middle. Esta informação é classificada para um nível de risco adequado de baixo, médio ou alto. Este nível de risco é então comparado com as licenças de nível de risco que estabeleceu no Intune. Com base nesta comparação, o acesso a certos recursos à sua escolha pode ser revogado enquanto o dispositivo está comprometido.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Dados que Intune recolhe para Defesa de Ameaças Móveis

Se ativado, a Intune recolhe informações de inventário de aplicações de dispositivos pessoais e corporativos e disponibiliza-as para os fornecedores de MTD irem buscar, como o Lookout for Work. Pode recolher o inventário de aplicações dos utilizadores de dispositivos com o iOS.

Este serviço é de participação ativa. Por predefinição, não são partilhadas informações do inventário de aplicações. Um administrador intune deve ativar **o App Sync para dispositivos iOS** nas definições do conector de defesa de ameaças móveis antes de qualquer informação de inventário de aplicações ser partilhada.

**Inventário de aplicações**  
Se ativar o App Sync para dispositivos iOS/iPadOS, os inventários de dispositivos iOS/iPadOS corporativos e pessoais são enviados para o seu prestador de serviços MTD. Os dados no inventário de aplicações incluem:

- ID da Aplicação
- Versão da Aplicação
- Versão Abreviada da Aplicação
- Nome da Aplicação
- Tamanho da Coleção de Pacotes de Aplicação
- Tamanho Dinâmico da Aplicação
- Se a aplicação é ou não validada
- Se a aplicação é ou não gerida

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Cenários de amostragem para dispositivos matriculados utilizando políticas de conformidade do dispositivo

Quando um dispositivo é considerado infetado pela solução de Defesa Contra Ameaças para Dispositivos Móveis:

![Imagem a mostrar um dispositivo infetado com a Defesa Contra Ameaças para Dispositivos Móveis](./media/mobile-threat-defense/MTD-image-1.png)

O acesso será concedido quando o dispositivo for remediado:

![Imagem a mostrar o acesso concedido pela Defesa Contra Ameaças para Dispositivos Móveis](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Cenários de amostragem para dispositivos não matriculados utilizando políticas de proteção de aplicações Intune

Quando um dispositivo é considerado infetado pela solução de Defesa Contra Ameaças para Dispositivos Móveis:<br>
imagem ![mostrando um dispositivo infetado de Defesa de Ameaças Móveis](./media/mobile-threat-defense/MTD-image-3.png)

O acesso será concedido quando o dispositivo for remediado:<br>
imagem ![mostrando um acesso de defesa de ameaça móvel concedido](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Você pode usar vários vendedores de Defesa Móvel com um único inquilino Intune. No entanto, quando dois ou mais fornecedores estiverem configurados para serem utilizados para a mesma plataforma, todos os dispositivos que executam essa plataforma devem instalar cada aplicação MTD e procurar ameaças. A não apresentação de uma varredura de qualquer aplicação configurada resulta na marcação do dispositivo como incompatível. 

## <a name="mobile-threat-defense-partners"></a>Parceiros de Defesa Contra Ameaças a Dispositivos Móveis

Saiba como pode proteger o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos com o:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
