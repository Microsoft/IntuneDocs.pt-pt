---
title: Discovered apps (Aplicações detetadas)
titleSuffix: Microsoft Intune
description: Entenda os detalhes sobre os aplicativos detectados que o Intune encontrou em um dispositivo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: eff4ccdc8b40da4d72394001b88446653ff71bd0
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564251"
---
# <a name="intune-discovered-apps"></a>Aplicativos descobertos do Intune

**Aplicativos descobertos** do Intune é uma lista de aplicativos detectados nos dispositivos registrados no Intune em seu locatário. Ele atua como um inventário de software para seu locatário. **Aplicativos descobertos** é um relatório separado dos relatórios de [instalação do aplicativo](apps-monitor.md) . Para dispositivos pessoais, o Intune nunca coleta informações sobre aplicativos que não são gerenciados. Em dispositivos corporativos, qualquer aplicativo que seja um aplicativo gerenciado ou não seja coletado para este relatório. Abaixo está a tabela que está mapeando o comportamento esperado. Em geral, o relatório é atualizado a cada 7 dias a partir do momento do registro (não uma atualização semanal para o locatário inteiro). A única exceção a esse período de atualização são as informações do aplicativo coletadas por meio da extensão de gerenciamento do Intune para aplicativos Win32, que são coletadas a cada 24 horas.

## <a name="monitor-discovered-apps-with-intune"></a>Monitorar aplicativos descobertos com o Intune

O Intune fornece uma lista agregada de aplicativos detectados nos dispositivos registrados no Intune em seu locatário.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **monitorar** > **aplicativos descobertos**.

>[!NOTE]
>Você pode exportar a lista de aplicativos descobertos para um arquivo. csv selecionando **Exportar** no painel **aplicativos descobertos** .
>
>Para aplicativos Win32 descobertos, não há nenhuma contagem de agregação no momento. Esse tipo de dados só pode ser exibido em uma base por dispositivo.

O Intune também fornece a lista de aplicativos descobertos para o dispositivo individual em seu locatário.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **todos os dispositivos**.
3. Selecione um dispositivo.
4. Para exibir os aplicativos detectados para este dispositivo, selecione **aplicativos descobertos** na seção **monitorar** .

## <a name="details-of-discovered-apps"></a>Detalhes de aplicativos descobertos

A lista a seguir fornece o tipo de plataforma de aplicativo, os aplicativos que são monitorados para dispositivos pessoais, os aplicativos que são monitorados para dispositivos da empresa e o ciclo de atualização. Para obter mais informações sobre os tipos de aplicativo com suporte pelo Intune, consulte [tipos de aplicativo em Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Platform | Para dispositivos de propriedade pessoal | Para dispositivos de propriedade da empresa | Ciclo de atualização |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (aplicativos Win32) Observação: [requer a extensão de gerenciamento do Intune](intune-management-extension.md) no dispositivo | Não Aplicável | Todos os aplicativos Win32 encontrados na lista Adicionar/remover programas | A cada 24 horas do registro do dispositivo |
| Windows 10 (aplicativos modernos) | Somente aplicativos modernos gerenciados | Todos os aplicativos modernos instalados no dispositivo | A cada 7 dias do registro do dispositivo |
| Windows 8.1 | Somente aplicativos gerenciados | Somente aplicativos gerenciados | A cada 7 dias do registro do dispositivo |
| Windows Phone 8 | Somente aplicativos gerenciados | Somente aplicativos gerenciados | A cada 7 dias do registro do dispositivo |
| Windows RT | Somente aplicativos gerenciados | Somente aplicativos gerenciados | A cada 7 dias do registro do dispositivo |
| iOS | Somente aplicativos gerenciados | Todos os aplicativos instalados no dispositivo | A cada 7 dias do registro do dispositivo |
| macOS | Todos os aplicativos instalados no dispositivo | Todos os aplicativos instalados no dispositivo | A cada 7 dias do registro do dispositivo |
| Android | Somente aplicativos gerenciados | Todos os aplicativos instalados no dispositivo | A cada 7 dias do registro do dispositivo |
| Android Enterprise | Somente aplicativos gerenciados | Somente aplicativos instalados no perfil de trabalho | A cada 7 dias do registro do dispositivo |

> [!NOTE]
> Dispositivos ingressados no Azure AD híbrido do Windows 10, conforme mostrado na carga de trabalho de gerenciamento de aplicativos no Configuration Manager, atualmente não coletam o inventário de aplicativos por meio da extensão de gerenciamento do Intune (IME) de acordo com o agendamento acima. Para atenuar esse problema, a carga de trabalho de gerenciamento de aplicativo em Configuration Manager deve ser alternada para o Intune para que o IME seja instalado no dispositivo (o IME é necessário para o inventário do Win32 e a implantação do PowerShell). Observe que todas as alterações ou atualizações desse comportamento são anunciadas no [desenvolvimento](../fundamentals/in-development.md) e/ou [novidades](../fundamentals/whats-new.md).

O número de aplicações detetadas pode não corresponder à contagem de estados de instalação da aplicação. As causas de possíveis inconsistências incluem:

- Uma alteração de destino de um aplicativo gerenciado instalado pode fazer com que a contagem de instalação no painel de status seja decrementada, mas permaneça relatada nos aplicativos detectados.
- Abranger múltiplas instâncias da mesma aplicação num inquilino irá resultar em contagens diferentes, devido à potencial sobreposição de utilizadores ou dispositivos. Cada instância da aplicação irá contabilizar os utilizadores sobrepostos, mas as aplicações detetadas apresentarão contagens duplicadas.
- As aplicações detetadas e o estado da aplicação são recolhidos em intervalos de tempo diferentes, o que pode provocar uma discrepância nas contagens de aplicações.

## <a name="next-steps"></a>Próximos passos

- [Tipos de aplicativo no Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitorar as informações e atribuições de aplicativo com Microsoft Intune](apps-monitor.md)
