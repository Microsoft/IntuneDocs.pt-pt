---
title: Como obter suporte para o Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenha suporte online e por telefone para subscrições pagas e de avaliação do Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf1e87d40459d194f2c4aa0ff702a137e45504ab
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59900116"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Como obter suporte para o Microsoft Intune

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

A Microsoft fornece suporte global técnico, de pré-vendas, de faturação e de subscrição para o Microsoft Intune. O suporte está disponível tanto online como por telefone para subscrições pagas ou de avaliação. O suporte técnico online está disponível em inglês e japonês. O suporte por telefone e o suporte de faturação online estão disponíveis em idiomas adicionais.

Enquanto administrador do Intune, pode utilizar a opção **Ajuda e Suporte** para enviar um pedido de suporte online do Intune a partir do portal do Azure. Para criar e gerir um incidente de suporte, a conta tem de estar atribuída a uma função do Microsoft Azure Active Directory (Microsoft Azure AD) que inclui a *ação* **microsoft.office365.supportTickets/allEntities/allTasks**. Para obter informações sobre funções do Microsoft Azure AD e as permissões que são necessários para criar um pedido de suporte, veja as [funções de administrador no Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal). 

**Problemas conhecidos na criação de incidentes de suporte**

Se a sua conta tiver as permissões necessárias, mas não conseguir aceder com êxito à Ajuda e Suporte, ou criar ou gerir um incidente de suporte, veja os seguintes problemas conhecidos e resoluções:  
- Token de utilizador obsoleto para a sua conta. Para resolver este problema, termine a sessão em todas as sessões de consola ativas, inicie sessão novamente e, em seguida, tente criar ou gerir um incidente de suporte. 
- Várias sessões ativas. Se tiver iniciado sessão com mais do que um utilizador ou sessão, termine a sessão de todas as consolas, exceto uma. Em seguida, com uma única sessão ativa, experimente criar ou gerir um incidente de suporte.

Mais ações que poderão ser necessárias para resolver problemas de acesso:
- Limpe todos os cookies da sessão do browser ativa e tente novamente criar ou gerir um incidente de suporte.
- Utilize uma sessão de navegação InPrivate para iniciar sessão no Intune e tente criar ou gerir um incidente de suporte.  

Se as soluções alternativas anteriores não ajudarem, aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com) e crie um pedido de suporte. Estamos atualmente a trabalhar numa correção que estará disponível no final do verão. 



>[!IMPORTANT]  
> Para obter suporte técnico para produtos de terceiros que funcionam com o Intune (como a Saaswedo, a Cisco ou a Lookout), contacte primeiro o fornecedor desse produto. Antes de abrir um pedido com o suporte do Intune, certifique-se de que configurou o outro produto corretamente.
>
> Para obter informações sobre a resolução de problemas relacionados com o Microsoft Intune, veja a [secção Resolução de problemas](help-desk-operators.md) da documentação do Intune.




## <a name="help-and-support-experience"></a>Experiência da ajuda e suporte
> [!TIP]   
> Uma nova experiência de Ajuda e suporte está disponível para todos os inquilinos. Se não vir esta nova experiência no inquilino, limpe a cache do browser e recarregue a página.

A experiência da Ajuda e suporte do Intune está disponível no [portal de Gestão de Dispositivos do Microsoft 365](http://devicemanagement.microsoft.com) e em todos os painéis (ou páginas) no Intune dentro do portal do Azure. 

![Painéis do Intune](./media/get-support/intune-blades.png)


Esta nova experiência é semelhante à que foi apresentada no [centro de administração do Microsoft 365](https://admin.microsoft.com/) e substitui a experiência da Ajuda e suporte anterior. 

Para aceder a Ajuda e suporte, utilize as seguintes opções:  
- **Dashboard de Gestão de Dispositivos:**
   - Selecione qualquer opção disponível para **Ajuda e suporte**
   - Selecione o ícone **?** no canto superior direito do portal

- **No portal do Azure:**
   - Selecione **Ajuda e suporte** em qualquer painel ou página do Intune

   Selecionar o ícone **?** no canto superior direito ou **Ajuda + suporte** no painel de navegação esquerdo em qualquer localização no portal do Azure abre a *Ajuda + suporte* no Azure. Para obter a melhor experiência possível, utilize *Ajuda e suporte* no painel do Intune.  

Com a nova experiência, obtém acesso à vista **Precisa de ajuda?**, conforme apresentada na seguinte imagem no dashboard Gestão de Dispositivos:  
![Dashboard da Gestão de Dispositivos e página Precisa de Ajuda?](./media/get-support/help-support-dashboard.png)

Nesta vista, pode realizar uma das seguintes ações:

1. [Especificar detalhes](#specify-details-about-an-issue) sobre o problema específico para o qual precisa de ajuda  
2. [Ver a ajuda sensível ao contexto](#view-context-sensitive-help) e soluções relacionadas que são baseadas em detalhes que especificou  
3. [Obter suporte](#get-support) por e-mail ou telefone  
4. [Ver processos de suporte](#view-support-cases) que tenha aberto anteriormente através deste novo fluxo de trabalho  

### <a name="specify-details-about-an-issue"></a>Especificar detalhes sobre um problema
Quando abre a Ajuda e suporte a partir de uma localização suportada pela nova experiência, a página **Precisa de ajuda?** é apresentada. Nesta página, pode especificar os detalhes sobre um problema. À medida que introduz detalhes, a consola fornece consultas comuns baseadas nas palavras-chave que utilizar. Selecione uma opção fornecida ou preencha a sua própria descrição do problema. Se introduzir a sua própria descrição, selecione **Obter ajuda** para a submeter. Após submeter uma consulta, a consola devolverá informações sensíveis ao contexto que podem ajudar a resolver o problema.

Seguem-se exemplos de consultas que poderá submeter:
  
- *Não é possível restaurar o dispositivo iOS*  
- *Não é possível criar uma política de acesso condicional*  

![Especificar o problema na página Precisa de Ajuda?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Ver a ajuda sensível ao contexto
Após selecionar uma opção fornecida ou submeter a sua própria consulta, os resultados sensíveis ao contexto são apresentados por baixo de **Ver soluções**. Estes resultados incluem orientação de ajuda autónoma do Intune e resultados adicionais devolvidos a partir de uma pesquisa na Web baseada nos critérios da consulta.  
![Ver resultados](./media/get-support/view-results.png)

### <a name="get-support"></a>Obter suporte
Se a orientação de ajuda autónoma ou baseada na Web não ajudar a resolver o problema, utilize a consola para abrir um problema de suporte por e-mail ou telefone.  
Na página **Precisa de ajuda?**, selecione a opção que pretende utilizar.  

- Para um pedido de e-mail, forneça o seu endereço de e-mail e, opcionalmente, pode adicionar anexos à sua submissão. Selecione **Enviar** para abrir o pedido.  

  ![Pedido de e-mail](./media/get-support/email-support.png)
  
- Para um pedido de telefone, forneça o seu número de telefone. Opcionalmente, pode incluir o seu endereço de e-mail e adicionar anexos à sua submissão. Selecione Telefonar-me para submeter o pedido.  

   ![Pedido de telefone](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>Ver processos de suporte
Selecione o botão de histórico para ver os incidentes de suporte que criou.  

![Ver processos de suporte](./media/get-support/view-support-tickets.png)

- Apenas os processos de suporte que abrir com o novo fluxo de trabalho serão visíveis a partir deste fluxo de trabalho. Para os ver, utilize a vista Ajuda e suporte na consola Gestão de Dispositivos ou num painel do Intune do portal do Azure. Estes processos têm números com oito dígitos. Também pode ver estes processos a partir do centro de administração do Microsoft 365.  

- Permanecem inalterados os processos que abriu, quando não utilizou a experiência de Suporte e ajuda do Intune. Para os ver, tem de utilizar uma vista da Ajuda e suporte que não faça parte da experiência do Intune ou no dashboard Gestão de Dispositivo. Estes processos têm números que começam com **117** ou **118** e têm 15 dígitos. Para os visualizar:

    1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone *?* no canto superior direito do portal e, em seguida, selecione *Ajuda + suporte* para aceder à página [Ajuda + suporte do Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. Na página **Ajuda + suporte**, pode ver a lista de **Pedidos de suporte recentes** e selecionar os mesmos para ver detalhes adicionais.


## <a name="azure-help--support-experience"></a>Experiência da Ajuda + suporte do Azure
As informações seguintes descrevem a experiência da Ajuda + suporte do Azure, que permanece acessível a partir do portal do Azure quando utiliza a **Ajuda + suporte** do painel de navegação esquerdo ou utiliza a opção **?** no canto superior direito do portal do Azure. A partir de janeiro de 2019, não será possível aceder à experiência da *Ajuda + suporte* do Azure a partir da *Ajuda e suporte* conforme apresentado nos painéis do Intune.  

### <a name="create-an-online-support-ticket"></a>Criar um pedido de suporte online

1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Imagem da ligação de ponto de interrogação com a ligação de Ajuda + suporte realçada](./media/azure-get-support.png)

2. Na página **Ajuda + suporte** do Azure, selecione **Novo pedido de suporte**.

   ![Imagem da ligação Novo pedido de suporte realçada na página de ajuda e suporte](media/azure-support-ticket-link.png)

3. No separador **Básico**, para a maioria dos problemas de suporte técnico do Intune, selecione as seguintes opções:
   - **Tipo de problema**: **Técnico**
   - **Subscrição**: <*a sua subscrição*>
   - **Serviço**: **Microsoft Intune**
   - **Tipo de problema**: escolha o tipo de problema no menu pendente.
   - **Subtipo de problema**: escolha o subtipo de problema no menu pendente.
   - **Assunto**: descreva resumidamente o problema para o qual pretende obter ajuda.

   ![Imagem do separador Básico na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-basics.png)

   escolha **Seguinte: Soluções** para continuar.
4. No separador **Soluções**, reveja os passos recomendados que podem ajudá-lo a resolver o seu problema sem enviar um pedido de suporte. Se pretender continuar a criar um pedido de suporte depois de verificar os passos, clique em **Seguinte: Detalhes**.

   ![Imagem do separador Soluções na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-solutions.png)
5. No separador **Detalhes**, preencha os detalhes para o seu problema, o método de suporte, as informações de contacto e clique em **Seguinte: Rever + criar**.

   ![Imagem do separador Detalhes na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-details.png)
6. Reveja as informações, verifique se estão corretas e escolha **Criar** para submeter o pedido de suporte.

   ![Imagem do separador Rever + criar na página Novo pedido de suporte](./media/get-support/help-new-support-case-create.png)

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>Se tiver alguma pergunta relacionada com a faturação ou subscrição, poderá criar um processo para obter suporte através do [centro de administração do Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Ver pedidos de suporte
Pode ver um pedido de suporte a partir do portal do Azure. Para tal:

1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. Na página **Ajuda + suporte**, pode ver a lista de **Pedidos de suporte recentes** e selecionar os mesmos para ver detalhes adicionais.

## <a name="additional-resources"></a>Recursos adicionais
- [Suporte de gestão de subscrição e faturação](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licenciamento em Volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Resolver problemas do Intune](help-desk-operators.md)
