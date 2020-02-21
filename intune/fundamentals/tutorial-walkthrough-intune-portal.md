---
title: Tutorial - Walkthrough Intune in the Azure portal
titleSuffix: Microsoft Intune
description: Neste tutorial, você irá visitar o Microsoft Intune para entender melhor como realizar tarefas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 203d243df3e8ae496e7ff78f20222fd361417c3d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514052"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutorial: Walkthrough da Microsoft Intune no portal Azure

[O Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contém mais de 100 serviços para o ajudar com uma variedade de cenários e possibilidades de computação em nuvem. O Microsoft Intune é um dos vários serviços disponíveis no Azure. Intune ajuda-o a garantir que os dispositivos, aplicações e dados da sua empresa cumprem os requisitos de segurança da sua empresa. Tem o controlo para definir quais os requisitos que precisam de ser verificados e o que acontece quando esses requisitos não são cumpridos. Pode encontrar o serviço Microsoft Intune no [portal do Azure](https://portal.azure.com). Compreender as funcionalidades disponíveis no Intune irá ajudá-lo a realizar várias tarefas de Gestão de Dispositivos Móveis (MDM) e Gestão de Aplicações Móveis (MAM).

Neste tutorial, irá:
> [!div class="checklist"]
> * Tour Microsoft Intune
> * Configure o portal Azure

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Browsers e sistemas operativos suportados](../supported-devices-browsers.md) 
- [Largura de banda e requisitos de configuração de rede](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode [inscrever-se numa conta de teste gratuita](free-trial-sign-up.md) para usar o Intune para a sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="tour-microsoft-intune"></a>Tour Microsoft Intune

Siga os passos abaixo para entender melhor Intune no portal Azure. Assim que completar o tour, terá uma melhor compreensão de algumas das principais áreas de Intune.

1. Abra um navegador e inscreva-se no [portal Intune](https://aka.ms/intuneportal). Se é novo em Intune, use a sua subscrição de teste gratuita.

    ![Screenshot do portal Microsoft Intune](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Quando abre o Intune ou qualquer outro serviço em Azure, o serviço é exibido num painel. Algumas das primeiras cargas de trabalho que pode utilizar no Intune incluem **Dispositivos,** **aplicações de clientes,** **Utilizadores**e **Grupos.** Uma carga de trabalho é simplesmente uma sub-área de um serviço. Quando seleciona a carga de trabalho, abre-se o painel como uma página inteira. Outras vidraças deslizam para fora do lado direito do painel quando abrem, e perto para revelar o painel anterior. Um painel também é referido como uma lâmina. 

    Por defeito, quando abrir Intune verá o painel de **visão geral.** Este painel fornece uma imagem geral da atribuição e do estado de conformidade do dispositivo, bem como o estado de instalação da aplicação.

2. A partir de [Intune,](https://aka.ms/intuneportal)selecione **a inscrição do Dispositivo** para apresentar detalhes sobre os dispositivos matriculados no seu inquilino Intune. Se você está começando com um novo inquilino Intune, você não terá nenhum dispositivo matriculado ainda. 

    ![Screenshot do painel de inscrição do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune permite-lhe gerir os dispositivos e aplicações da sua força de trabalho, incluindo a forma como acedem aos dados da sua empresa. Para utilizar este serviço de gestão de dispositivos móveis (MDM), os dispositivos devem ser matriculados primeiro em Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune. 

    Existem vários métodos para inscrever os dispositivos da sua força de trabalho no Intune. Cada método depende da propriedade do dispositivo (pessoal ou corporativo), do tipo de dispositivo (iOS/iPadOS, Windows, Android) e dos requisitos de gestão (resets, afinidade, bloqueio). No entanto, antes de poder ativar a inscrição do dispositivo, tem de configurar a sua infraestrutura Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md). Para mais informações sobre como preparar o seu ambiente Intune (inquilino), consulte [Configurar Intune](setup-steps.md). Assim que tiver o seu inquilino intune pronto, pode inscrever dispositivos. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](../enrollment/device-enrollment.md)

3. A partir de [Intune,](https://aka.ms/intuneportal)selecione a conformidade do **Dispositivo** para mostrar detalhes sobre a conformidade com os dispositivos geridos pela Intune. Verá detalhes semelhantes à seguinte imagem.

    ![Screenshot do painel de conformidade do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Os requisitos de conformidade são essencialmente regras, tais como exigir um PIN do dispositivo ou exigir encriptação do dispositivo. As políticas de conformidade do dispositivo definem as regras e definições que um dispositivo deve seguir para ser considerada conforme. Para utilizar a conformidade do dispositivo, deve ter:
    - Uma subscrição Premium intune e um Azure Ative Directory (Azure AD)
    - Dispositivos que executam uma plataforma suportada
    - Os dispositivos devem ser matriculados em Intune
    - Dispositivos que estejam matriculados num utilizador ou sem utilizador primário.
    
    Para mais informações, consulte Iniciar as políticas de [conformidade do dispositivo em Intune](../protect/device-compliance-get-started.md).

4. A partir de [Intune,](https://aka.ms/intuneportal)selecione a **configuração do Dispositivo** para visualizar detalhes sobre os perfis do dispositivo no Intune.

    ![Screenshot do painel de configuração do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Pode criar perfis para diferentes dispositivos e diferentes plataformas, incluindo iOS/iPadOS, Android e Windows. Em seguida, pode usar o Intune para aplicar o perfil em dispositivos da sua organização.   

    Para obter mais informações sobre a configuração do dispositivo, consulte [as definições de funcionalidades de Aplicação nos seus dispositivos utilizando perfis de dispositivos no Microsoft Intune](../configuration/device-profiles.md).

5. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Dispositivos** para mostrar detalhes sobre os dispositivos inscritos do seu inquilino Intune. Se estiver a começar com um novo alistamento Intune, ainda não terá nenhum dispositivo matriculado.

    ![Screenshot do painel de inscrição do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    O painel **de dispositivos** fornece detalhes sobre os dispositivos matriculados do seu inquilino. Pode clicar em **todos os dispositivos** para apresentar uma lista de dispositivos para o seu inquilino Intune.

6. A partir de [Intune,](https://aka.ms/intuneportal)selecione **aplicações do Cliente** para exibir o estado de instalação da aplicação.

    ![Screenshot do painel de aplicações do cliente](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune. O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha. Para obter mais informações sobre a adição e atribuição de apps, consulte [adicionar aplicações ao Microsoft Intune](../apps/apps-add.md) e [atribuir aplicações a grupos com](../apps/apps-deploy.md)o Microsoft Intune .

7. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Acesso Condicional** para mostrar detalhes sobre as políticas de acesso.

    ![Screenshot do painel de acesso condicional](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    O Acesso Condicional refere-se a formas de controlar os dispositivos e aplicações que podem ligar-se aos seus e-mails e recursos da empresa. Para conhecer o Acesso Condicional baseado em dispositivos e aplicativos, e encontrar cenários comuns para usar o Acesso Condicional com Intune, consulte [o What's Conditional Access?](../protect/conditional-access.md)

8. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Utilizadores** para mostrar detalhes sobre os utilizadores que incluiu no Intune. Estes utilizadores são a força de trabalho da sua empresa.

    ![Screenshot do painel dos Utilizadores](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Pode adicionar utilizadores diretamente ao Intune ou sincronizar os utilizadores a partir do seu Diretório Ativo no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode dar aos utilizadores permissões adicionais para aceder ao Intune. Para mais informações, consulte [Adicionar utilizadores e conceder permissão administrativa para Intune](users-add.md).

9. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Grupos** para mostrar detalhes sobre os grupos Azure Ative Directory (Azure AD) incluídos no Intune. Como administrador intune, utiliza grupos para gerir dispositivos e utilizadores.

    ![Screenshot do painel de grupos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Pode criar grupos de acordo com as suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para muitos utilizadores ou implementar aplicações para um conjunto de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar utilizadores e dispositivos](../groups-add.md).

10. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Ajuda e suporte** para pedir ajuda. Como administrador de TI, pode utilizar a opção **de Ajuda e Suporte** para pesquisar e visualizar soluções, bem como arquivar um bilhete de suporte on-line para Intune. 

    ![Screenshot do painel de ajuda e suporte](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Para criar um bilhete de apoio, a sua conta deve ser atribuída como administrador a desempenhar funções de administrador no Diretório Ativo azure. As funções de administrador incluem, **administrador intune,** **administrador global,** e **administrador de serviços.** Para mais informações, consulte [Como obter suporte para o Microsoft Intune](../get-support.md).

11. A partir de [Intune,](https://aka.ms/intuneportal)selecione Estatuto de **Inquilino** para mostrar detalhes sobre o seu inquilino Intune.

    ![Screenshot do painel do Estatuto do Inquilino](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Os detalhes do estado do inquilino incluem o estado do conector, a saúde do serviço Intune e as notícias Intune. Se houver algum problema com o seu inquilino ou com o próprio Intune, encontrará detalhes no painel do Estatuto do **Arrendatário.** Para mais informações, consulte [Intune Tenant Status](../tenant-status.md).

12. A partir de [Intune,](https://aka.ms/intuneportal)selecione **Troubleshoot** para chegar a um atalho em dicas de resolução de problemas, solicitando apoio ou verificando o estado de Intune. Esta informação é específica do utilizador Intune que seleciona.

    ![Screenshot do painel Troubleshoot](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Para mais informações sobre resolução de problemas dentro do Intune, consulte Use o portal de resolução de [problemas para ajudar os utilizadores da sua empresa.](../help-desk-operators.md)

## <a name="configure-the-azure-portal"></a>Configure o portal Azure

O Azure permite-lhe personalizar e configurar a vista do portal.

### <a name="change-the-sidebar"></a>Mude a barra lateral

A **barra lateral** no lado esquerdo do portal do Azure mostra-lhe uma lista de todos os serviços do Azure disponíveis. A vista predefinida desta lista abrangente pode ser alterada para que mantenha uma vista persistente dos serviços mais relevantes para si. As informações abaixo utilizam o Intune como o exemplo de um serviço a adicionar ao topo da lista.

![Um utilizador a procurar o Microsoft Intune na lista "Mais serviços".](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. Selecione **Todos os serviços** na barra lateral no lado esquerdo da página.
2. Procure **Intune** na caixa de filtragem.
3. Selecione a **estrela** para adicionar o Intune à parte inferior da lista dos seus serviços preferidos.
4. Paire o cursor sobre o serviço Intune. Selecione e arraste o Intune através dos **três pontos verticais** à direita do nome do serviço.

### <a name="change-the-dashboard"></a>Mude o painel de instrumentos

A sua página de destino predefinida é o **dashboard**. Esta é a página onde personaliza os seus mosaicos para apresentar as informações que lhe são mais relevantes.

![Um imagem do novo dashboard genérico. Apresenta a barra lateral com todos os serviços à esquerda e o dashboard principal ao centro. Os botões de modificação do dashboard encontram-se na parte superior, com mosaicos que disponibilizam o acesso a todos os recursos, tutoriais de início rápido, o estado de funcionamento do serviço e o Azure Marketplace.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

Para modificar o seu dashboard atual, selecione o botão **Editar dashboard**. Se não quiser alterar o seu dashboard predefinido, também pode criar um **Novo dashboard**. Criar um novo dashboard disponibiliza-lhe um dashboard vazio e privado com a **Galeria de Mosaicos**, que lhe permite adicionar ou reordenar mosaicos. Pode encontrar mosaicos através da categoria **Geral**, do **Tipo**, da funcionalidade **Procurar** ou através de um **Grupo de recursos** ou **Etiqueta**.

Também pode adicionar mosaicos diretamente ao seu dashboard a partir de qualquer botão de **reticências** e ao selecionar **Afixar ao dashboard**.

![Um grande plano da localização Utilizadores e Grupos > Todos os grupos no Intune, com a opção "Afixar ao dashboard" visível na extremidade direita de um grupo.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

Esta funcionalidade ser-lhe-á mais relevante após adicionar mais conteúdos, tais como grupos e utilizadores, ao Intune.

## <a name="next-steps"></a>Próximos passos

Para começar a correr rapidamente no Microsoft Intune, passe pelo Intune Quickstarts, criando primeiro uma conta Intune gratuita.

> [!div class="nextstepaction"]
> [Quickstart: Experimente o Microsoft Intune gratuitamente](free-trial-sign-up.md)
