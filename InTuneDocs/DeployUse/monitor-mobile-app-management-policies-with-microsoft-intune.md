---
title: "Monitorizar políticas de gestão de aplicações móveis com o Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ded7bd6c971a9448ad6e6492ebc5e42dfcb5d76e
ms.openlocfilehash: 99b50bd040bbbdfa3ad7937d7703700526c9c4d5


---

# Monitorizar políticas de gestão de aplicações móveis com o Microsoft Intune
Depois de ter configurado uma política de MAM e tê-la aplicado aos utilizadores, pode monitorizar o estado de conformidade no [portal do Azure](https://portal.azure.com). O portal do Azure inclui informações sobre os utilizadores afetados pela política, o estado de conformidade e quaisquer problemas que possam estar a ocorrer nos utilizadores finais.
## Vista de resumo
No painel **Gestão de aplicações móveis do Intune**, pode ver um resumo do estado de conformidade, tal como descrito abaixo:


![Mosaico de resumo no painel de gestão de aplicações móveis do Intune](../media/mam-azure-portal-user-status-summary.png)

-   **UTILIZADORES:** o número total de utilizadores na sua empresa que estão a utilizar as aplicações associadas à política.

-   **GERIDO POR POLÍTICA:** O número de utilizadores que utilizaram, pelo menos, uma das aplicações no contexto profissional.

-   **NENHUMA POLÍTICA:** o número de utilizadores que estão a utilizar as aplicações associadas à política, mas não são visados pela política.  Pode considerar adicionar estes utilizadores à sua política.

- **Utilizadores sinalizados:** o número de utilizadores com problemas. Atualmente, apenas os utilizadores com dispositivos com jailbreak são reportados como **Utilizadores sinalizados**.


## Vista detalhada
Pode aceder à vista detalhada do resumo clicando nos mosaicos **Estado de utilizador** e **Utilizadores sinalizados**.

### Estado de utilizador
Pode procurar um único utilizador e ver o estado de conformidade desse utilizador. O painel **Relatório da aplicação** apresenta as seguintes informações para um utilizador selecionado:
- Dispositivos associados à conta de utilizador
- Aplicações com a política de MAM no dispositivo
- Estado:

  **Com entrada dada:** isto significa que a política foi implementada no utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.

  **Sem entrada dada:** isto significa que a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.

Para ver o relatório para um utilizador, siga estes passos:

**Passo 1:** para selecionar um utilizador, clique no mosaico Resumo ou escolha a opção **RELATÓRIO DA APLICAÇÃO POR UTILIZADOR** no painel **Definições**, conforme apresentado abaixo:

![Opção Relatório da aplicação no painel Definições](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

**Passo 2:** abre o painel **Relatório da aplicação**. Escolha **Selecionar utilizador** para procurar um utilizador do Azure Active Directory.

![Opção Selecionar utilizador no painel Relatório da aplicação](../media/mam-azure-portal-app-reporting-select-user.png)

**Passo 3:** após selecionar o utilizador na lista, verá os detalhes do estado de conformidade desse utilizador.

![Detalhes do relatório da aplicação](../media/mam-azure-portal-app-reporting-by-user.png)
### Utilizadores sinalizados
A vista detalhada apresenta a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma do dispositivo e um carimbo de data/hora.  

### Consulte também
[Gerir a transferência de dados entre aplicações iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

[Experiência de utilizador final para aplicações com MAM ativada](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


