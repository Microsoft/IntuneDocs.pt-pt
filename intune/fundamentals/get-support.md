---
title: Como obter suporte para o Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenha suporte online e por telefone para subscrições pagas e de avaliação do Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86ea53ef2def05f622ef49fa37965d3f93d796d9
ms.sourcegitcommit: 4bf23327af734a9811d555fbd566c31239e2acd6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/29/2019
ms.locfileid: "72999713"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Como obter suporte para o Microsoft Intune

A Microsoft fornece suporte global técnico, de pré-vendas, de faturação e de subscrição para o Microsoft Intune. O suporte está disponível tanto online como por telefone para subscrições pagas ou de avaliação. O suporte técnico online está disponível em inglês e japonês. O suporte por telefone e o suporte de faturação online estão disponíveis em idiomas adicionais.

Enquanto administrador do Intune, pode utilizar a opção **Ajuda e Suporte** para enviar um pedido de suporte online do Intune a partir do portal do Azure. Para criar e gerenciar um incidente de suporte, sua conta deve ter uma função Azure Active Directory (Azure AD) que inclua a *ação* **Microsoft. office365. supportTickets**. Para obter informações sobre funções do Microsoft Azure AD e as permissões que são necessários para criar um pedido de suporte, veja as [funções de administrador no Microsoft Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Para obter suporte técnico para produtos de terceiros que funcionam com o Intune (como a Saaswedo, a Cisco ou a Lookout), contacte primeiro o fornecedor desse produto. Antes de abrir um pedido com o suporte do Intune, certifique-se de que configurou o outro produto corretamente.
>
> Para obter informações sobre a resolução de problemas relacionados com o Microsoft Intune, veja a [secção Resolução de problemas](help-desk-operators.md) da documentação do Intune.


## <a name="help-and-support-experience"></a>Experiência da ajuda e suporte

A experiência da Ajuda e suporte do Intune está disponível no [portal de Gestão de Dispositivos do Microsoft 365](https://devicemanagement.microsoft.com) e em todos os painéis (ou páginas) no Intune dentro do portal do Azure.

A experiência de *ajuda e suporte* é semelhante à experiência vista no [centro de administração Microsoft 365](https://admin.microsoft.com/)e substitui a *ajuda + suporte*anterior, que permanece em vigor para outros serviços no Azure.

Para aceder a Ajuda e suporte, utilize as seguintes opções:

- **Dashboard de Gestão de Dispositivos:**
  - Depois de selecionar uma área de recurso para o Intune, selecione a opção **ajuda e suporte**.
  - Em qualquer nó no portal de gerenciamento de dispositivos, selecione o **?** no canto superior direito do portal e, em seguida, use a lista suspensa para selecionar o serviço com o qual deseja obter ajuda. O **?** no portal de gerenciamento de dispositivos dá suporte a vários serviços e você deve selecionar o serviço específico para o qual deseja obter assistência.  

    ![Selecione seu serviço](./media/get-support/select-a-service.png)

    Depois de selecionar um serviço, você verá a página de *ajuda e suporte* para esse serviço, em que você pode especificar detalhes para [encontrar soluções](#find-solutions) para um problema específico.

    Quando os resultados de sua pesquisa não parecerem corresponder às expectativas de seu serviço, verifique se o serviço correto foi selecionado. A seleção de serviço aparece logo após *a ajuda e o suporte*.  Se o serviço certo não tiver sido selecionado, clique em *selecionar um serviço* para retornar à lista suspensa de seleção de serviço.

    ![Confirmar seu serviço](./media/get-support/confirm-your-service-selection.png)

- **No portal do Azure:**
  - Selecione **ajuda e suporte** em qualquer folha ou página do Intune.

  > [!NOTE]  
  > Se sua instância do Intune estiver hospedada na nuvem privada para o governo, também conhecida como uma nuvem soberanas como Azure governamental, consulte [suporte do Intune para nuvem privada para o governo](#intune-support-for-private-cloud-for-government), mais adiante neste artigo. A experiência de *ajuda e suporte* do Intune não estará disponível na nuvem privada para o governo até o momento neste ano.

  Quando você abre a ajuda e o suporte, o portal exibe a janela **precisa de ajuda?** :

  ![Exibir a janela de ajuda necessária](./media/get-support/need-help.png)

  No canto superior esquerdo, há três ícones que você pode selecionar para abrir painéis diferentes da janela precisa de *ajuda?* . O painel que você vê é identificado pelo sublinhado.

  Os clientes com um contrato de suporte **Premier** ou **unificado** têm [Opções adicionais](#premier-and-unified-support-customers) de suporte e podem ver uma faixa em *necessidade de ajuda?* que se assemelham à imagem a seguir: ![faixa Premier](./media/get-support/premier-banner.png)

  *Precisa de ajuda?* Abre o painel *Localizar soluções* . No entanto, se você tiver um caso de suporte ativo, a janela será aberta no painel *solicitações de serviço* , onde você poderá exibir detalhes sobre os casos de suporte ativo e fechado.

### <a name="find-solutions"></a>Encontrar soluções

![Selecione o painel Localizar soluções](./media/get-support/find-solutions.png)

No painel *Localizar soluções* , especifique alguns detalhes sobre um problema na caixa de texto fornecida. Com base no texto que você fornece sobre um problema, o painel é preenchido com informações que são possíveis correspondências. Você também receberá links para artigos recomendados que podem ajudá-lo a resolver o problema.

Quando uma correspondência forte é encontrada para os detalhes que você descreve, as dicas de solução de problemas podem aparecer diretamente na janela *precisa de ajuda?* .

Por exemplo, você pode inserir **erros de sincronização de senha**. Os resultados incluem orientação de solução de problemas diretamente no painel e links para artigos recomendados de nossa biblioteca de documentação.

![Exibir informações de solução de problemas](./media/get-support/troubleshooting-insights.png)

### <a name="contact-support"></a>Contatar o suporte

![Selecione o painel de suporte do contato](./media/get-support/contact-support.png)

No painel de *suporte de contato* , você pode enviar uma solicitação de assistência. Esse painel estará disponível depois que você fornecer algumas palavras-chave básicas no painel *Localizar soluções* .

Ao solicitar assistência, forneça uma descrição do problema com o máximo de detalhes necessário.  Depois de confirmar seu telefone e enviar informações de contato por email, selecione o método de contato que você preferir. A janela exibe um tempo de resposta para cada método de contato, que lhe dá uma expectativa de quando você será contatado. Antes de enviar sua solicitação, anexe arquivos como logs ou capturas de tela que podem ajudar a preencher detalhes sobre o problema.

![Contatar o formulário de suporte](./media/get-support/contact-support-form.png)

Depois de preencher as informações necessárias, selecione **entre em contato comigo** para enviar a solicitação.

### <a name="service-requests"></a>Solicitações de serviço

![Selecione o painel solicitações de serviço](./media/get-support/service-requests.png)

O painel *solicitações de serviço* exibe seu histórico de casos. Os casos ativos estão na parte superior da lista, com problemas fechados também disponíveis para revisão.

![Exibir sua lista de solicitações de serviço](./media/get-support/service-requests-pane.png)

Se você tiver um número de caso de suporte ativo, poderá inseri-lo aqui para ir para esse problema, ou pode selecionar qualquer incidente na lista de incidentes ativos e fechados para exibir mais informações sobre ele.

Quando terminar de exibir detalhes de um incidente, selecione a seta para a esquerda que aparece na parte superior da janela de solicitação de serviço logo acima dos ícones para os ícones de três *necessidades ajuda?* do painel. A seta voltar retorna a exibição para a lista de incidentes de suporte que você abriu.

### <a name="premier-and-unified-support-customers"></a>Clientes de suporte Premier e unificado

Como cliente com um contrato de suporte **Premier** ou **unificado** , você pode especificar uma severidade para o problema e agendar um retorno de chamada de suporte para um horário e dia específicos. Essas opções estão disponíveis quando você abre ou envia um novo problema e quando você edita um caso de suporte ativo.

**Severidade** – as opções para especificar a severidade de um problema dependem do seu contrato de suporte:

- *Premier*: severidade de A, B ou C
- *Unificado*: crítico ou não crítico

A seleção de uma gravidade **a ou um** problema **crítico** limita você a um caso de suporte por telefone, que fornece a opção mais rápida para obter suporte.

**Agendamento de retorno de chamada** -você pode solicitar um retorno de chamada em um dia e hora específicos.

## <a name="azure-help--support-experience"></a>Experiência da Ajuda + suporte do Azure

Quando você usa o painel de navegação esquerdo **ajuda + suporte**ou usa o **?** no canto superior direito do portal do Azure, você abre a experiência de ajuda + suporte do Azure, que é distinta da experiência de ajuda e suporte do Intune.

A partir de abril de 2019, não é possível acessar a experiência de *ajuda + suporte* do Azure para obter assistência com o Intune, a menos que sua assinatura esteja em uma nuvem privada para o governo. 

Se sua instância do Intune não for executada em uma nuvem privada para o governo, navegar pela ajuda do Azure *+ support* redireciona você para a experiência de *ajuda e suporte* do Intune para criar e gerenciar incidentes de suporte.

## <a name="intune-support-for-private-cloud-for-government"></a>Suporte do Intune para nuvem privada para o governo

Quando sua assinatura do Intune é hospedada na nuvem privada para o governo, que também é conhecida como nuvem soberanas como o Azure governamental, você ainda não tem acesso à ajuda e à experiência de suporte mais recentes do Intune.  Em vez disso, use as informações a seguir para obter suporte para o Intune.

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
