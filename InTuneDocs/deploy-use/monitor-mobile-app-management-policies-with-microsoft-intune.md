---
title: "Monitorizar políticas de MAM com o Microsoft Intune | Documentos da Microsoft"
description: "Veja quantos utilizadores têm a política e consulte mais detalhes."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: 2a18ad7226c6fc6de0277f1f20443ea64dc8b918


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Monitorizar políticas de gestão de aplicações móveis com o Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Depois de ter configurado uma política de gestão de aplicações móveis (MAM) e tê-la aplicado aos utilizadores, pode monitorizar o estado de conformidade no [portal do Azure](https://portal.azure.com). O portal do Azure inclui informações sobre os utilizadores afetados pela política, o estado de conformidade e quaisquer problemas que possam estar a ocorrer nos utilizadores.
## <a name="summary-view"></a>Vista de resumo
No painel **Gestão de aplicações móveis do Intune**, pode ver um resumo do estado de conformidade:


![Mosaico de resumo no painel de gestão de aplicações móveis do Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Utilizadores:** o número total de utilizadores na sua empresa que estão a utilizar as aplicações associadas à política.

-   **GERIDO POR POLÍTICA:** o número de utilizadores que utilizaram, pelo menos, uma das aplicações no contexto profissional.

-   **NENHUMA POLÍTICA:** o número de utilizadores que estão a utilizar as aplicações associadas à política, mas não são visados pela política. Poderá considerar adicionar estes utilizadores à sua política.

- **Utilizadores sinalizados:** o número de utilizadores que estão com problemas. Atualmente, apenas os utilizadores com dispositivos com jailbreak são reportados como **Utilizadores sinalizados**.


## <a name="detailed-view"></a>Vista detalhada
Pode aceder à vista detalhada do resumo ao selecionar os mosaicos **Estado de utilizador** e **Utilizadores sinalizados**.

### <a name="user-status"></a>Estado de utilizador
Pode procurar um único utilizador e ver o estado de conformidade do mesmo. O painel **Relatório da aplicação** mostra as seguintes informações para um utilizador selecionado:
- Dispositivos associados à conta de utilizador

- Aplicações com a política de MAM no dispositivo

- Estado:

  - **Com entrada dada:** a política foi implementada no utilizador e a aplicação foi utilizada no contexto profissional pelo menos uma vez.

  - **Sem entrada dada:** a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.

>[!NOTE]
> Se o utilizador que procurou não tiver a política de MAM implementada, verá uma mensagem a informar que não existem aplicações segmentadas para esse utilizador.

Para ver o relatório para um utilizador, siga estes passos:

1.  Para selecionar um utilizador, selecione o mosaico **Resumo** ou selecione a opção **RELATÓRIO DA APLICAÇÃO POR UTILIZAODR** no painel **Definições**:

    ![Opção Relatório da aplicação no painel Definições](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. No painel **Relatório da aplicação** que abrir, selecione **Selecionar utilizador** para procurar um utilizador do Azure Active Directory.

    ![Opção Selecionar utilizador no painel Relatório da aplicação](../media/mam-azure-portal-app-reporting-select-user.png)

3. Selecione o utilizador na lista. Irá ver os detalhes do estado de conformidade do utilizador.

    ![Detalhes do relatório da aplicação](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>Utilizadores sinalizados
A vista detalhada mostra a mensagem de erro, a aplicação que foi acedida quando ocorreu o erro, a plataforma do dispositivo e um carimbo de data/hora.  

### <a name="see-also"></a>Consulte também
[Gerir a transferência de dados entre aplicações iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [O que esperar quando a sua aplicação Android é gerida por políticas de MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [O que esperar quando a sua aplicação iOS é gerida por políticas de MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


