---
title: "Monitorizar políticas de MAM com o Microsoft Intune | Microsoft Intune"
description: "Veja quantos utilizadores têm a política e desagregue para descobrir mais detalhes."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 644860abcd351d24f08d7a517a3a4b5f44824689
ms.openlocfilehash: 1d22d26c1a1c52dda4f9b01658d22f8de8187f0f


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

>[!NOTE]
> Se o utilizador que procurou não tiver a política de MAM implementada, verá uma mensagem a informar que não existem aplicações segmentadas para esse utilizador.

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



<!--HONumber=Jul16_HO4-->


