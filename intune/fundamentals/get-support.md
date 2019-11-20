---
title: Como obter suporte para o Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenha suporte online e por telefone para subscrições pagas e de avaliação do Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14ff8ad2d41a6f2235c18f155e3a5b865e3a32e4
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199301"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Como obter suporte para o Microsoft Intune

A Microsoft fornece suporte global técnico, de pré-vendas, de faturação e de subscrição para o Microsoft Intune. O suporte está disponível tanto online como por telefone para subscrições pagas ou de avaliação. O suporte técnico online está disponível em inglês e japonês. O suporte por telefone e o suporte de faturação online estão disponíveis em idiomas adicionais.

Enquanto administrador do Intune, pode utilizar a opção **Ajuda e Suporte** para enviar um pedido de suporte online do Intune a partir do portal do Azure. To create and manage a support incident, your account must have an Azure Active Directory (Azure AD) role that includes the *action* **microsoft.office365.supportTickets**. Para obter informações sobre funções do Microsoft Azure AD e as permissões que são necessários para criar um pedido de suporte, veja as [funções de administrador no Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Para obter suporte técnico para produtos de terceiros que funcionam com o Intune (como a Saaswedo, a Cisco ou a Lookout), contacte primeiro o fornecedor desse produto. Antes de abrir um pedido com o suporte do Intune, certifique-se de que configurou o outro produto corretamente.
>
> Para obter informações sobre a resolução de problemas relacionados com o Microsoft Intune, veja a [secção Resolução de problemas](help-desk-operators.md) da documentação do Intune.


## <a name="help-and-support-experience"></a>Experiência da ajuda e suporte

A experiência da Ajuda e suporte do Intune está disponível no [portal de Gestão de Dispositivos do Microsoft 365](https://devicemanagement.microsoft.com) e em todos os painéis (ou páginas) no Intune dentro do portal do Azure.

The *Help and support* experience is similar to the experience seen in the [Microsoft 365 admin center](https://admin.microsoft.com/), and replaces the previous *Help + support*, which remains in place for other services in Azure.

> [!TIP]
> Starting November 18, 2019, an updated and streamlined in-console experience for getting help and support is rolling out to tenants. If this new experience isn't available for you yet, it will be soon.

### <a name="options-to-access-help-and-support"></a>Options to access Help and support

- **In the Azure portal:**

  - Select **Help and support** from any Intune blade or page.

  > [!NOTE]  
  > If your instance of Intune is hosted on the private cloud for government, also known as a sovereign cloud like Azure Government, see [Intune support for private cloud for government](#intune-support-for-private-cloud-for-government), later in this article. The Intune *Help and support* experience won’t be available on the private cloud for government until next year.

- **From the Device Management Dashboard:**
  - After you've selected a feature area for Intune, select the option for **Help and support**.
  - From any node in the Device Management portal, select the **?** icon in the upper-right corner of the portal, and then use the drop-down to select the service you want help with. The **?** icon in the Device Management portal supports multiple services, and you must select the specific service you want assistance for.  

    ![Select your service](./media/get-support/select-a-service.png)

    After you select a service, you'll see the *Help and support* page for that service where you can specify details to [find solutions](#find-solutions) for a specific problem.

    When the results of your search don't seem to match expectations for your service, check to ensure the correct service was selected. The service selection appears just after *Help and support*.  If the right service wasn't selected, click on *Select a service* to return to the service selection drop-down.

    ![Confirm your service](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>The support experience

  When you open Help and Support, the portal displays the **Need help?** window:

  ![View the need help window](./media/get-support/need-help.png)

  In the left top corner there are three icons that you can select to open different panes of the *Need Help?* window. The pane your viewing is identified by the underline.

  Customers with a **Premier** or **Unified** support contract have [additional options](#premier-and-unified-support-customers) for support, and see a banner in *Need help?* that resembles the following image: ![Premier banner](./media/get-support/premier-banner.png)

  *Need Help?* opens to the *Find Solutions* pane. However, if you have an active support case the window opens to the *Service requests* pane where you can view details about your active and closed support cases.

#### <a name="find-solutions"></a>Find solutions

![Select the find solutions pane](./media/get-support/find-solutions.png)

On the *Find solutions* pane, specify a few details about an issue in the provided text box. Based on the text you provide about an issue, the pane populates with insights that are potential matches. You'll also get links to recommended articles that might help you resolve the issue.

When a strong match is found for the details you describe, troubleshooting tips can appear right in the *Need help?* window.

For example, you might enter **Password synchronization errors**. The results include troubleshooting guidance directly in the pane, and links to recommended articles from our documentation library.

![View troubleshooting insights](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Contact support

![Select the contact support pane](./media/get-support/contact-support.png)

From the *contact support* pane, you can submit a request for assistance. This pane is available after you provide some basic keywords on the *find solutions* pane.

When requesting assistance, provide a description of the problem with as much detail as needed.  After confirming your phone and email contact information, select the method of contact you prefer. The window displays a response time for each contact method, which gives you an expectation of when you'll be contacted. Before submitting your request, attach files like logs or screenshots that can help fill in details about the issue.

![Contact support form](./media/get-support/contact-support-form.png)

After you fill in the required information, select **Contact me** to submit the request.

#### <a name="service-requests"></a>Service requests

![Select the service requests pane](./media/get-support/service-requests.png)

The *Service requests* pane displays your case history. Active cases are at the top of the list, with closed issues also available for review.

![View your service request list](./media/get-support/service-requests-pane.png)

If you have an active support case number, you can enter it here to jump to that issue, or you can select any incident from the list of active and closed incidents to view more information about it.

When you’re done viewing details for an incident, select the left arrow that appears at the top of the service request window just above the icons for the three *Need Help?* pane icons. The back arrow returns the display to the list of support incidents you’ve opened.

#### <a name="premier-and-unified-support-customers"></a>Premier and Unified support customers

As a customer with a **Premier** or **Unified** support contract, you can specify a severity for your issue, and schedule a support callback for a specific time and day. These options are available when you open or submit a new issue and when you edit an active support case.

**Severity** - The options to specify the severity of an issue depend on your support contract:

- *Premier*: Severity of A, B, or C
- *Unified*: Critical, or non-critical

Selecting either a severity **A** or **Critical** issue limits you to a phone support case, which provides the fastest option to get support.

**Callback schedule** - You can request a callback on a specific day and time.

## <a name="azure-help--support-experience"></a>Experiência da Ajuda + suporte do Azure

You can no longer use the Azure *Help + support* experience to get assistance with Intune, unless your subscription is on a private cloud for government.
If your instance of Intune doesn't run on a private cloud for government, navigating through Azure *Help + support* redirects you to the Intune *Help and support* experience to create and manage support incidents:

When you use the left navigation pane **Help + support**, or use the **?** option to open the *Help* pane and then select **Help + support**, you open the Azure *Help + support* page. 


From this page select **+ New support request** to open the *Basics* tab of the *Help + support + New support request* page.

![Help + support](./media/get-support/help-plus-support.png)

On this page:

- For *Issue type*, select  **Technical**.
- For *Service*, select **Microsoft Intune**.

  You are then presented with a link that redirects you to the [Intune Help and Support page](https://aka.ms/intunehelpsupport).
  
  ![New support request](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Intune support for private cloud for government

When your Intune subscription hosted on the private cloud for government, which is also known as a sovereign cloud like Azure Government, you don’t yet have access to the newer Intune Help and support experience.  Instead, use the following information go get support for Intune.

### <a name="create-an-online-support-ticket"></a>Criar um pedido de suporte online

>[!IMPORTANT]
> As *Help and support* transitions to a new system which is not yet available for the private cloud for government, when you create a support incident, the portal identifies a support case that uses a 15 digit identification number. When the 15-digit case is created, a mirror of that case is created for use by Microsoft Support. This mirror case is created in a new support system, uses an 8-digit case ID, and is used by support services to track all work and communications for your support incident. Shortly after your 15-digit case is created, you’ll receive an email that identifies the 8-digit number of the mirrored support case that is used by support services.
>
> Support personal work and communicate from the 8-digit support case, and only use the 8-digit support case to log communications and track incident progress. Therefore, you’ll receive email updates from that 8-digit support case that serve as your case-work track record. No details are logged into the 15-digit support incident. When support concludes and the 8-digit support case closes, that status is reflected in by the 15-digit support case that you can view from within the azure portal.  No other updates or status changes should be expected for the 15-digit support case.
>
> When transitions between support tools completes later this year, the support experience Intune hosted on the government cloud will resemble the default *Help and support* experience that’s currently available for Intune subscriptions hosted on the public cloud.

1. Inicie sessão no portal do Azure (<https://portal.azure.us>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Imagem da ligação de ponto de interrogação com a ligação de Ajuda + suporte realçada](./media/get-support/azure-get-support.png)

2. Na página **Ajuda + suporte** do Azure, selecione **Novo pedido de suporte**.

   ![Imagem da ligação Novo pedido de suporte realçada na página de ajuda e suporte](./media/get-support/azure-support-ticket-link.png)

3. No separador **Básico**, para a maioria dos problemas de suporte técnico do Intune, selecione as seguintes opções:
   - **Tipo de problema**: **técnico**
   - **Subscrição**: <*a sua subscrição*>
   - **Serviço**: **Microsoft Intune**
   - **Problem type**: Choose your problem type from the drop-down menu.
   - **Problem subtype**: Choose the problem subtype from the drop-down menu.
   - **Subject**: Briefly describe the issue you want help with.

   ![Imagem do separador Básico na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-basics.png)

   Choose **Next: Solutions** to continue.
4. No separador **Soluções**, reveja os passos recomendados que podem ajudá-lo a resolver o seu problema sem enviar um pedido de suporte. If you still want to create a support request after looking through the steps, click **Next: Details**.

   ![Imagem do separador Soluções na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-solutions.png)
5. On the **Details** tab, fill out the details for your problem, the support method, your contact information, and then click **Next: Review + create**.

   ![Imagem do separador Detalhes na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-details.png)
6. Reveja as informações, verifique se estão corretas e escolha **Criar** para submeter o pedido de suporte.

   ![Imagem do separador Rever + criar na página Novo pedido de suporte](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Se tiver alguma pergunta relacionada com a faturação ou subscrição, poderá criar um processo para obter suporte através do [centro de administração do Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Ver pedidos de suporte  

You can view your support requests from within the Azure portal. However, limited information is available.  To view your incidents:

1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. On the **Help + support** page, you can view the list of **Recent support requests**.

   > [!IMPORTANT]  
   > Private cloud for government customers can only view the 15-digit support case number, and the incident status. All case communications and tracking of work or alerts are sent by email and reference the 8-digit support case number that is created as a mirror of the support case opened from within the Intune console.

## <a name="additional-resources"></a>Recursos adicionais  

- [Suporte de gestão de subscrição e faturação](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licenciamento em Volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Resolver problemas do Intune](help-desk-operators.md)
