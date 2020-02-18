---
title: Discovered apps (Aplicações detetadas)
titleSuffix: Microsoft Intune
description: Compreenda detalhes sobre as aplicações detetadas que Intune encontrou num dispositivo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: a727cf03f53ee003c27708a04ad475f0b370c487
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415008"
---
# <a name="intune-discovered-apps"></a>Intune aplicativos descobertos

Intune **discovered apps** é uma lista de aplicações detetadas nos dispositivos inscritos intune no seu inquilino. Funciona como um inventário de software para o seu inquilino. **As aplicações descobertas** são um relatório separado dos relatórios de instalação da [aplicação.](apps-monitor.md) Para dispositivos pessoais, a Intune nunca recolhe informações sobre aplicações que não são geridas. Em dispositivos corporativos, qualquer aplicação quer seja uma aplicação gerida ou não é recolhida para este relatório. Abaixo está a tabela mapeando o comportamento esperado. Em geral, o relatório atualiza-se a cada 7 dias do momento da inscrição (não é uma atualização semanal para todo o inquilino). A única exceção a este período de atualização é a informação de aplicação recolhida através da Extensão de Gestão Intune para aplicações Win32, que é recolhida a cada 24 horas.

## <a name="monitor-discovered-apps-with-intune"></a>Monitor descobriu aplicações com Intune

Intune fornece uma lista agregada de aplicações detetadas nos dispositivos inscritos intune no seu inquilino.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Monitor** > **Discovered apps**.

>[!NOTE]
>Pode exportar a lista de aplicações descobertas para um ficheiro .csv selecionando **exportação** do painel de **aplicações Descobertos.**
>
>Para as aplicações Win32 descobertas, não existe atualmente uma contagem agregada. Este tipo de dados só pode ser visualizado por dispositivo.

Intune também fornece a lista de aplicativos descobertos para o dispositivo individual no seu inquilino.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Todos os Dispositivos**.
3. Selecione um dispositivo.
4. Para visualizar aplicações detetadas para este dispositivo, selecione **Aplicações Descobertas** na secção **Monitor.**

## <a name="details-of-discovered-apps"></a>Detalhes de aplicações descobertas

A lista que se segue fornece o tipo de plataforma de aplicações, as aplicações que são monitorizadas para dispositivos pessoais, as aplicações que são monitorizadas para dispositivos da empresa e o ciclo de atualização. Para obter mais informações sobre os tipos de aplicações suportados pela Intune, consulte os tipos de [aplicações no Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Platform | Para dispositivos pessoais | Para dispositivos pertencentes à empresa | Ciclo de atualização |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Aplicações Win32) NOTA: Requer extensão de [gestão intune](intune-management-extension.md) no dispositivo | Não Aplicável | Apenas aplicações geridas | A cada 24 horas da inscrição do dispositivo |
| Windows 10 (Aplicações Modernas) | Apenas aplicações modernas geridas | Todas as aplicações modernas instaladas no dispositivo | A cada 7 dias da inscrição do dispositivo |
| Windows 8,1 | Apenas aplicações geridas | Apenas aplicações geridas | A cada 7 dias da inscrição do dispositivo |
| Windows Phone 8 | Apenas aplicações geridas | Apenas aplicações geridas | A cada 7 dias da inscrição do dispositivo |
| Windows RT | Apenas aplicações geridas | Apenas aplicações geridas | A cada 7 dias da inscrição do dispositivo |
| iOS/iPadOS | Apenas aplicações geridas | Todas as aplicações instaladas no dispositivo | A cada 7 dias da inscrição do dispositivo |
| macOS | Apenas aplicações geridas | Todas as aplicações instaladas no dispositivo | A cada 7 dias da inscrição do dispositivo |
| Android | Apenas aplicações geridas | Todas as aplicações instaladas no dispositivo | A cada 7 dias da inscrição do dispositivo |
| Android Enterprise | Apenas aplicações geridas | Apenas aplicações instaladas no Perfil de Trabalho | A cada 7 dias da inscrição do dispositivo |

> [!NOTE]
> - O Windows 10 Hybrid Azure AD juntou-se a dispositivos, como mostra a carga de trabalho de gestão de aplicações no Gestor de Configuração, não recolhendo atualmente o inventário de aplicações através da Extensão de Gestão Intune (IME) de acordo com o horário acima referido. Para mitigar este problema, a carga de trabalho de gestão de aplicações no Gestor de Configuração deve ser transferida para Intune para que o IME seja instalado no dispositivo (a IME é necessária para o inventário Win32 e implementação powerShell). Note que quaisquer alterações ou atualizações sobre este comportamento são anunciadas [em desenvolvimento](../fundamentals/in-development.md) e/ou quais [as novidades](../fundamentals/whats-new.md).
> - Os dispositivos macOS de propriedade pessoal matriculados antes de novembro de 2019 podem continuar a mostrar todas as aplicações instaladas no dispositivo até que os dispositivos estejam novamente matriculados.
> - Android Enterprise Totalmente Gerido e Dedicado não exibe aplicações descobertas.

O número de aplicações detetadas pode não corresponder à contagem de estados de instalação da aplicação. As causas de possíveis inconsistências incluem:

- Uma mudança de alvo de uma aplicação gerida instalada pode fazer com que a contagem de instalações no painel de estado se decre, mas permanece reportada nas aplicações detetadas.
- Abranger múltiplas instâncias da mesma aplicação num inquilino irá resultar em contagens diferentes, devido à potencial sobreposição de utilizadores ou dispositivos. Cada instância da aplicação irá contabilizar os utilizadores sobrepostos, mas as aplicações detetadas apresentarão contagens duplicadas.
- As aplicações detetadas e o estado da aplicação são recolhidos em intervalos de tempo diferentes, o que pode provocar uma discrepância nas contagens de aplicações.

## <a name="next-steps"></a>Próximos passos

- [Tipos de aplicativos no Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitorize informações e atribuições de aplicativos com o Microsoft Intune](apps-monitor.md)
