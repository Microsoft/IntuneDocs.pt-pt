---
title: Como obter suporte para o Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenha suporte online e por telefone para subscrições pagas e de avaliação do Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91627a47f9dccfb436e64aaadeeb392648dff821
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585305"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Como obter suporte para o Microsoft Intune  

[!INCLUDE [azure_portal](../../intune-classic/includes/note-for-both-portals.md)]  
  
A Microsoft fornece suporte global técnico, de pré-vendas, de faturação e de subscrição para o Microsoft Intune. O suporte está disponível tanto online como por telefone para subscrições pagas ou de avaliação. O suporte técnico online está disponível em inglês e japonês. O suporte por telefone e o suporte de faturação online estão disponíveis em idiomas adicionais.

Enquanto administrador do Intune, pode utilizar a opção **Ajuda e Suporte** para enviar um pedido de suporte online do Intune a partir do portal do Azure. Para criar e gerenciar um incidente de suporte, sua conta deve ter uma função Azure Active Directory (Azure AD) que inclua a *ação* **Microsoft. office365. supportTickets/tickets/Manage**. Para obter informações sobre funções do Microsoft Azure AD e as permissões que são necessários para criar um pedido de suporte, veja as [funções de administrador no Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Para obter suporte técnico para produtos de terceiros que funcionam com o Intune (como a Saaswedo, a Cisco ou a Lookout), contacte primeiro o fornecedor desse produto. Antes de abrir um pedido com o suporte do Intune, certifique-se de que configurou o outro produto corretamente.
>
> Para obter informações sobre a resolução de problemas relacionados com o Microsoft Intune, veja a [secção Resolução de problemas](help-desk-operators.md) da documentação do Intune.

## <a name="known-issues-for-creating-support-incidents"></a>Problemas conhecidos para a criação de incidentes de suporte  

Se a sua conta tiver as permissões necessárias, mas não conseguir aceder com êxito à Ajuda e Suporte, ou criar ou gerir um incidente de suporte, veja os seguintes problemas conhecidos e resoluções:  
- Token de utilizador obsoleto para a sua conta. Para resolver este problema, termine a sessão em todas as sessões de consola ativas, inicie sessão novamente e, em seguida, tente criar ou gerir um incidente de suporte. 
- Várias sessões ativas. Se você tiver entrado com mais de um usuário ou sessão, saia de todos, exceto um console. Em seguida, com uma única sessão ativa, experimente criar ou gerir um incidente de suporte.

Mais ações que poderão ser necessárias para resolver problemas de acesso:
- Limpe todos os cookies da sessão do browser ativa e tente novamente criar ou gerir um incidente de suporte.
- Utilize uma sessão de navegação InPrivate para iniciar sessão no Intune e tente criar ou gerir um incidente de suporte.  

Se as soluções alternativas anteriores não ajudarem, aceda ao [centro de administração do Microsoft 365](https://admin.microsoft.com) e crie um pedido de suporte. No momento, estamos trabalhando em uma correção que estará disponível no final de verão.  

## <a name="help-and-support-experience"></a>Experiência da ajuda e suporte  

A experiência da Ajuda e suporte do Intune está disponível no [portal de Gestão de Dispositivos do Microsoft 365](https://devicemanagement.microsoft.com) e em todos os painéis (ou páginas) no Intune dentro do portal do Azure. 

![Painéis do Intune](./media/get-support/intune-blades.png)


A experiência de *ajuda e suporte* é semelhante à experiência vista no [centro de administração Microsoft 365](https://admin.microsoft.com/)e substitui a *ajuda + suporte*anterior, que permanece em vigor para outros serviços no Azure. 

Para aceder a Ajuda e suporte, utilize as seguintes opções:  
- **Dashboard de Gestão de Dispositivos:**
  - Depois de selecionar uma área de recurso para o Intune, selecione a opção **ajuda e suporte**.
  - Em qualquer nó no portal de gerenciamento de dispositivos, selecione o **?** no canto superior direito do portal e, em seguida, use a lista suspensa para selecionar o serviço com o qual deseja obter ajuda. O **?** no portal de gerenciamento de dispositivos dá suporte a vários serviços e você deve selecionar o serviço específico para o qual deseja obter assistência.  

    ![Selecione seu serviço](./media/get-support/select-a-service.png)

    Depois de selecionar um serviço, você verá a página de *ajuda e suporte* para esse serviço, em que é possível [especificar detalhes](#specify-details-about-an-issue) sobre o problema específico com o qual você deseja obter ajuda.  

    Se os resultados da sua pesquisa não parecerem corresponder às expectativas de seu serviço, verifique se o serviço correto foi selecionado. A seleção de serviço aparece logo após *a ajuda e o suporte*.  Se o serviço certo não tiver sido selecionado, clique em *selecionar um serviço* para retornar à lista suspensa de seleção de serviço.   

    ![Confirmar seu serviço](./media/get-support/confirm-your-service-selection.png) 


- **No portal do Azure:**
  - Selecione **Ajuda e suporte** em qualquer painel ou página do Intune

  Na portal do Azure, se você selecionar a opção **?** ícone do canto superior direito ou **ajuda + suporte** no painel de navegação do lado esquerdo, você abre *ajuda + suporte* para o Azure. Da *ajuda + suporte*do Azure, você não pode abrir um incidente de suporte do Intune diretamente, mas pode acessar a página de *ajuda e suporte* do Intune fazendo as seguintes ações: 
  1. Selecione nova solicitação de suporte.
  2. Para tipo de problema, especifique técnico.
  3. Para serviço, especifique Microsoft Intune.
  4. Selecione a página link de ajuda e suporte do Intune.

> [!NOTE]  
> Se sua instância do Intune estiver hospedada na nuvem privada para entidades governamentais, também conhecida como nuvem soberanas como Azure governamental, consulte [suporte do Intune para nuvem privada para o governo](#intune-support-for-private-cloud-for-government), mais adiante neste artigo. A experiência de *ajuda e suporte* do Intune não estará disponível na nuvem privada para o governo até o momento neste ano. 


Quando você abre a *ajuda e o suporte*, o portal exibe uma exibição que depende se você tem ou não incidentes de suporte ativos, e quando você tem suporte Premier, alguns elementos e opções adicionais:
- **Nenhum incidente de suporte ativo**: você verá a página **precisa de ajuda?** , como visto na imagem a seguir do painel de gerenciamento de dispositivos.  
- **Incidentes de suporte ativos**: você verá a página [tíquetes de suporte](#view-support-cases) , que exibe a lista de seus incidentes ativos.  
- **Contrato de suporte Premier**: sua experiência é a mesma das duas primeiras opções, embora você veja os seguintes elementos adicionais sobre a necessidade de ajuda? Web 
  - Depois que o título da página **precisar de ajuda?** , você verá a faixa suporte Premier:  
    faixa de suporte do ![Premier ](./media/get-support/premier-banner.png)
  - Na seção **obter suporte** da página, você pode definir o nível de **severidade** inicial ao criar uma solicitação de serviço por telefone.


![Painel de gerenciamento de dispositivos e a ajuda necessária? Web](./media/get-support/help-support-dashboard.png)

Nesta vista, pode realizar uma das seguintes ações:

1. [Especificar detalhes](#specify-details-about-an-issue) sobre o problema específico para o qual precisa de ajuda  
2. [Ver a ajuda sensível ao contexto](#view-context-sensitive-help) e soluções relacionadas que são baseadas em detalhes que especificou  
3. [Obter suporte](#get-support) por e-mail ou telefone  
4. [Ver processos de suporte](#view-support-cases) que tenha aberto anteriormente através deste novo fluxo de trabalho  

### <a name="specify-details-about-an-issue"></a>Especificar detalhes sobre um problema 

Quando abre a Ajuda e suporte a partir de uma localização suportada pela nova experiência, a página **Precisa de ajuda?** é apresentada. Nesta página, pode especificar os detalhes sobre um problema. À medida que introduz detalhes, a consola fornece consultas comuns baseadas nas palavras-chave que utilizar. Selecione uma opção fornecida ou preencha a sua própria descrição do problema. Se introduzir a sua própria descrição, selecione **Obter ajuda** para a submeter. Após submeter uma consulta, a consola devolverá informações sensíveis ao contexto que podem ajudar a resolver o problema.

Seguem-se exemplos de consultas que poderá submeter:
  
- *Não é possível restaurar o dispositivo iOS*  
- *Não é possível criar política de acesso condicional*  

![Especificar o problema na página Precisa de Ajuda?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Ver a ajuda sensível ao contexto 

Após selecionar uma opção fornecida ou submeter a sua própria consulta, os resultados sensíveis ao contexto são apresentados por baixo de **Ver soluções**. Estes resultados incluem orientação de ajuda autónoma do Intune e resultados adicionais devolvidos a partir de uma pesquisa na Web baseada nos critérios da consulta.  
![Ver resultados](./media/get-support/view-results.png)

### <a name="get-support"></a>Obter suporte 

Se a orientação de ajuda autónoma ou baseada na Web não ajudar a resolver o problema, utilize a consola para abrir um problema de suporte por e-mail ou telefone.  
Na página **Precisa de ajuda?** , selecione a opção que pretende utilizar.  

  > [!NOTE] 
  > As solicitações de email para suporte não estão disponíveis para todos os locatários.  

- Para um pedido de e-mail, forneça o seu endereço de e-mail e, opcionalmente, pode adicionar anexos à sua submissão. Selecione **Enviar** para abrir o pedido. 

  ![Pedido de e-mail](./media/get-support/email-support.png)
  
- Para um pedido de telefone, forneça o seu número de telefone. Opcionalmente, pode incluir o seu endereço de e-mail e adicionar anexos à sua submissão. Selecione Telefonar-me para submeter o pedido.  



   ![Pedido de telefone](./media/get-support/phone-support.png)

**Suporte Premier**:  
Se você tiver um contrato de suporte Premier, terá as mesmas opções para criar um incidente de suporte por telefone. Você também pode especificar a **severidade** para o retorno de chamada de suporte e optar por criar o tíquete de suporte em relação ao seu contrato de missão crítica.  

![Opções de suporte Premier](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Ver processos de suporte  

Selecione o botão de histórico para ver os incidentes de suporte que criou.  

![Ver processos de suporte](./media/get-support/view-support-tickets.png)

- Apenas os processos de suporte que abrir com o novo fluxo de trabalho serão visíveis a partir deste fluxo de trabalho. Para os ver, utilize a vista Ajuda e suporte na consola Gestão de Dispositivos ou num painel do Intune do portal do Azure. Estes processos têm números com oito dígitos. Também pode ver estes processos a partir do centro de administração do Microsoft 365.  

- Permanecem inalterados os processos que abriu, quando não utilizou a experiência de Suporte e ajuda do Intune. Para os ver, tem de utilizar uma vista da Ajuda e suporte que não faça parte da experiência do Intune ou no dashboard Gestão de Dispositivo. Estes processos têm números que começam com **117** ou **118** e têm 15 dígitos. Para os visualizar:

    1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone *?* no canto superior direito do portal e, em seguida, selecione *Ajuda + suporte* para aceder à página [Ajuda + suporte do Azure](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. Na página **Ajuda + suporte**, pode ver a lista de **Pedidos de suporte recentes** e selecionar os mesmos para ver detalhes adicionais.
 

## <a name="azure-help--support-experience"></a>Experiência da Ajuda + suporte do Azure 

Quando você usa o painel de navegação esquerdo **ajuda + suporte**ou usa o **?** no canto superior direito do portal do Azure, você abre a experiência de ajuda + suporte do Azure, que é distinta da experiência de ajuda e suporte do Intune.  

A partir de abril de 2019, não é possível acessar a experiência de *ajuda + suporte* do Azure para obter assistência com o Intune, a menos que sua assinatura esteja em uma nuvem privada para entidades governamentais.  

Se sua instância do Intune não for executada em uma nuvem privada para o governo, navegar pela ajuda do Azure *+ support* redireciona você para a experiência de *ajuda e suporte* do Intune para criar e gerenciar incidentes de suporte.  


## <a name="intune-support-for-private-cloud-for-government"></a>Suporte do Intune para nuvem privada para o governo  

Quando sua assinatura do Intune é hospedada na nuvem privada para entidades governamentais, que também é conhecida como nuvem soberanas como Azure governamental, você ainda não tem acesso à ajuda e à experiência de suporte mais recentes do Intune.  Em vez disso, use as informações a seguir para obter suporte para o Intune. 


### <a name="create-an-online-support-ticket"></a>Criar um pedido de suporte online 

>[!IMPORTANT]    
> Como *ajuda e suporte* faz a transição para um novo sistema que ainda não está disponível para a nuvem privada para o governo, quando você cria um incidente de suporte, o portal identifica um caso de suporte que usa um número de identificação de 15 dígitos. Quando o caso de 15 dígitos é criado, um espelho desse caso é criado para ser usado pelo Suporte da Microsoft. Esse caso de espelho é criado em um novo sistema de suporte, usa uma ID de caso de 8 dígitos e é usado pelos serviços de suporte para acompanhar todo o trabalho e as comunicações de seu incidente de suporte. Logo após a criação do seu caso de 15 dígitos, você receberá um email que identifica o número de 8 dígitos do caso de suporte espelhado que é usado pelos serviços de suporte.  
> 
> Dê suporte a trabalho pessoal e comunique-se com o caso de suporte de 8 dígitos e use apenas o caso de suporte de 8 dígitos para registrar comunicações e acompanhar o progresso do incidente. Portanto, você receberá atualizações de email desse caso de suporte de 8 dígitos que serve como seu registro de faixa de trabalho de caso. Nenhum detalhe é registrado no incidente de suporte de 15 dígitos. Quando o suporte é concluído e o caso de suporte de 8 dígitos é fechado, esse status é refletido pelo caso de suporte de 15 dígitos que você pode exibir no portal do Azure.  Nenhuma outra atualização ou alteração de status deve ser esperada para o caso de suporte de 15 dígitos.  
> 
> Quando as transições entre as ferramentas de suporte forem concluídas neste ano, a experiência de suporte do Intune hospedada na nuvem governamental se assemelhará à *Ajuda padrão e à* experiência de suporte que está disponível atualmente para as assinaturas do Intune hospedadas no nuvem pública.  


1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Imagem da ligação de ponto de interrogação com a ligação de Ajuda + suporte realçada](./media/get-support/azure-get-support.png)

2. Na página **Ajuda + suporte** do Azure, selecione **Novo pedido de suporte**.

   ![Imagem da ligação Novo pedido de suporte realçada na página de ajuda e suporte](./media/get-support/azure-support-ticket-link.png)

3. No separador **Básico**, para a maioria dos problemas de suporte técnico do Intune, selecione as seguintes opções:
   - **Tipo de problema**: **técnico**
   - **Subscrição**: <*a sua subscrição*>
   - **Serviço**: **Microsoft Intune**
   - **Tipo de problema**: escolha o tipo de problema no menu suspenso.
   - **Subtipo de problema**: escolha o subtipo de problema no menu suspenso.
   - **Assunto**: Descreva brevemente o problema com o qual você deseja obter ajuda.

   ![Imagem do separador Básico na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-basics.png)

   Escolha **Avançar: soluções** para continuar.
4. No separador **Soluções**, reveja os passos recomendados que podem ajudá-lo a resolver o seu problema sem enviar um pedido de suporte. Se você ainda quiser criar uma solicitação de suporte depois de examinar as etapas, clique em **Avançar: detalhes**.

   ![Imagem do separador Soluções na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-solutions.png)
5. Na guia **detalhes** , preencha os detalhes do problema, o método de suporte, suas informações de contato e clique em **Avançar: revisar + criar**.

   ![Imagem do separador Detalhes na Ajuda + suporte – Nova página de pedido de suporte](./media/get-support/help-new-support-case-details.png)
6. Reveja as informações, verifique se estão corretas e escolha **Criar** para submeter o pedido de suporte.

   ![Imagem do separador Rever + criar na página Novo pedido de suporte](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Se tiver alguma pergunta relacionada com a faturação ou subscrição, poderá criar um processo para obter suporte através do [centro de administração do Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Ver pedidos de suporte  

Você pode exibir suas solicitações de suporte de dentro do portal do Azure. No entanto, informações limitadas estão disponíveis.  Para exibir seus incidentes: 

1. Inicie sessão no portal do Azure (<https://portal.azure.com>) com as suas credenciais de administrador do Intune, selecione o ícone **?** no canto superior direito do portal e, em seguida, selecione **Ajuda + suporte** para aceder à página [Ajuda + suporte do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. Na página **ajuda + suporte** , você pode exibir a lista de **solicitações de suporte recentes**.

   > [!IMPORTANT]  
   > A nuvem privada para clientes do governo só pode exibir o número do caso de suporte de 15 dígitos e o status do incidente. Todas as comunicações de caso e acompanhamento de trabalho ou alertas são enviados por email e fazem referência ao número de caso de suporte de 8 dígitos que é criado como um espelho do caso de suporte aberto de dentro do console do Intune.   

## <a name="additional-resources"></a>Recursos adicionais  

- [Suporte de gestão de subscrição e faturação](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Licenciamento em Volume](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Resolver problemas do Intune](help-desk-operators.md)
