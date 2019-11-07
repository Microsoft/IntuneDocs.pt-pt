---
title: Tutorial-Guia de instruções do Intune no portal do Azure
titleSuffix: Microsoft Intune
description: Neste tutorial, você fará um tour Microsoft Intune para entender melhor como realizar tarefas.
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
ms.openlocfilehash: 9197d4f96eae1041b00b07110ef421a12a4fe338
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712990"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutorial: passo a passos de Microsoft Intune no portal do Azure

O [Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contém mais de 100 serviços para ajudá-lo com uma variedade de cenários e possibilidades de computação em nuvem. Microsoft Intune é um dos vários serviços disponíveis no Azure. O Intune ajuda a garantir que os dispositivos, aplicativos e dados da sua empresa atendam aos requisitos de segurança da sua empresa. Você tem o controle para definir quais requisitos precisam ser verificados e o que acontece quando esses requisitos não são atendidos. Pode encontrar o serviço Microsoft Intune no [portal do Azure](https://portal.azure.com). A compreensão dos recursos disponíveis no Intune ajudará você a realizar várias tarefas de MDM (gerenciamento de dispositivo móvel) e MAM (gerenciamento de aplicativo móvel).

Neste tutorial, você vai:
> [!div class="checklist"]
> * Microsoft Intune de Tour
> * Configurar o portal do Azure

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Browsers e sistemas operativos suportados](../supported-devices-browsers.md) 
- [Largura de banda e requisitos de configuração de rede](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, você pode [se inscrever para uma conta de avaliação gratuita](free-trial-sign-up.md) para usar o Intune para sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="tour-microsoft-intune"></a>Microsoft Intune de Tour

Siga as etapas abaixo para entender melhor o Intune no portal do Azure. Depois de concluir o Tour, você terá uma compreensão melhor de algumas das principais áreas do Intune.

1. Abra um navegador e entre no portal do [Intune](https://aka.ms/intuneportal). Se você for novo no Intune, use sua assinatura de avaliação gratuita.

    ![Captura de tela do portal de Microsoft Intune](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Quando você abre o Intune ou qualquer outro serviço no Azure, o serviço é exibido em um painel. Algumas das primeiras cargas de trabalho que você pode usar no Intune incluem **dispositivos**, **aplicativos cliente**, **usuários**e **grupos**. Uma carga de trabalho é simplesmente uma subárea de um serviço. Quando você seleciona a carga de trabalho, ela abre esse painel como uma página inteira. Outros painéis deslizam do lado direito do painel quando são abertos e fecham para revelar o painel anterior. Um painel também é chamado de folha. 

    Por padrão, ao abrir o Intune, você verá o painel **visão geral** . Esse painel fornece um instantâneo Visual geral da atribuição de dispositivo e do status de conformidade, bem como o status de instalação do aplicativo.

2. No [Intune](https://aka.ms/intuneportal), selecione **registro de dispositivo** para exibir detalhes sobre os dispositivos registrados no seu locatário do Intune. Se você estiver começando com um novo locatário do Intune, ainda não terá nenhum dispositivo registrado. 

    ![Captura de tela do painel de registro do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    O Intune permite que você gerencie os dispositivos e aplicativos da sua força de funcionários, incluindo como eles acessam os dados da empresa. Para usar esse serviço de MDM (gerenciamento de dispositivo móvel), os dispositivos devem primeiro ser registrados no Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune. 

    Há vários métodos para registrar os dispositivos da sua força de funcionários no Intune. Cada método depende da propriedade do dispositivo (pessoal ou empresarial), do tipo de dispositivo (iOS, Windows, Android) e dos requisitos de gestão (reposições, afinidade, bloqueio). No entanto, antes de poder habilitar o registro do dispositivo, você deve configurar sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md). Para obter mais informações sobre como preparar seu ambiente do Intune (locatário), consulte [Configurar o Intune](setup-steps.md). Quando o seu locatário do Intune estiver pronto, você poderá registrar dispositivos. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](../enrollment/device-enrollment.md)

3. No [Intune](https://aka.ms/intuneportal), selecione **conformidade do dispositivo** para exibir detalhes sobre a conformidade de dispositivos gerenciados pelo Intune. Você verá detalhes semelhantes à imagem a seguir.

    ![Captura de tela do painel de conformidade do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Os requisitos de conformidade são essencialmente regras, como exigir um PIN de dispositivo ou exigir criptografia de dispositivo. As políticas de conformidade do dispositivo definem as regras e configurações que um dispositivo deve seguir para ser considerado em conformidade. Para usar a conformidade do dispositivo, você deve ter:
    - Um Intune e uma assinatura do Azure Active Directory (Azure AD) Premium
    - Dispositivos que executam uma plataforma com suporte
    - Os dispositivos devem ser registrados no Intune
    - Dispositivos registrados em um usuário ou nenhum usuário primário.
    
    Para obter mais informações, consulte Introdução [às políticas de conformidade do dispositivo no Intune](../protect/device-compliance-get-started.md).

4. No [Intune](https://aka.ms/intuneportal), selecione **configuração do dispositivo** para exibir detalhes sobre perfis de dispositivo no Intune.

    ![Captura de tela do painel de configuração do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Pode criar perfis para diferentes dispositivos e diferentes plataformas, incluindo iOS, Android e Windows. Em seguida, você pode usar o Intune para aplicar o perfil aos dispositivos em sua organização.   

    Para obter mais informações sobre a configuração do dispositivo, consulte [aplicar configurações de recursos em seus dispositivos usando perfis de dispositivo no Microsoft Intune](../configuration/device-profiles.md).

5. No [Intune](https://aka.ms/intuneportal), selecione **dispositivos** para exibir detalhes sobre os dispositivos registrados do seu locatário do Intune. Se você estiver começando com uma nova inscrição do Intune, ainda não terá nenhum dispositivo registrado.

    ![Captura de tela do painel de registro do dispositivo](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    O painel **dispositivos** fornece detalhes sobre os dispositivos registrados do seu locatário. Você pode clicar em **todos os dispositivos** para exibir uma lista de dispositivos para seu locatário do Intune.

6. No [Intune](https://aka.ms/intuneportal), selecione **aplicativos cliente** para exibir o status de instalação do aplicativo.

    ![Captura de tela do painel aplicativos cliente](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune. O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha. Para obter mais informações sobre como adicionar e atribuir aplicativos, consulte [Add apps to Microsoft Intune](../apps/apps-add.md) and [assign apps to groups with Microsoft Intune](../apps/apps-deploy.md).

7. No [Intune](https://aka.ms/intuneportal), selecione **acesso condicional** para exibir detalhes sobre as políticas de acesso.

    ![Captura de tela do painel de acesso condicional](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    O acesso condicional refere-se a maneiras que você pode controlar os dispositivos e aplicativos que têm permissão para se conectar ao seu email e aos recursos da empresa. Para saber mais sobre o acesso condicional baseado em dispositivo e com base no aplicativo, e encontrar cenários comuns para usar o acesso condicional com o Intune, consulte [o que é o acesso condicional?](../protect/conditional-access.md)

8. No [Intune](https://aka.ms/intuneportal), selecione **usuários** para exibir detalhes sobre os usuários que você incluiu no Intune. Esses usuários são a força de obra da sua empresa.

    ![Captura de tela do painel usuários](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Você pode adicionar usuários diretamente ao Intune ou sincronizar usuários do seu Active Directory local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Você também pode conceder aos usuários permissões adicionais para acessar o Intune. Para obter mais informações, consulte [Adicionar usuários e conceder permissão administrativa ao Intune](users-add.md).

9. No [Intune](https://aka.ms/intuneportal), selecione **grupos** para exibir detalhes sobre os grupos de Azure Active Directory (Azure AD) incluídos no Intune. Como administrador do Intune, você usa grupos para gerenciar dispositivos e usuários.

    ![Captura de tela do painel grupos](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Você pode configurar grupos para atender às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, você pode definir políticas para muitos usuários ou implantar aplicativos em um conjunto de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar usuários e dispositivos](../groups-add.md).

10. No [Intune](https://aka.ms/intuneportal), selecione **ajuda e suporte** para solicitar ajuda. Como administrador de ti, você pode usar a opção **ajuda e suporte** para pesquisar e exibir soluções, bem como o arquivo de um tíquete de suporte online para o Intune. 

    ![Captura de tela do painel ajuda e suporte](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Para criar um tíquete de suporte, sua conta deve ser atribuída como uma função de administrador no Azure Active Directory. As funções de administrador incluem, **administrador do Intune**, **administrador global**e **administrador de serviços**. Para obter mais informações, consulte [como obter suporte para Microsoft Intune](../get-support.md).

11. No [Intune](https://aka.ms/intuneportal), selecione **status do locatário** para exibir detalhes sobre seu locatário do Intune.

    ![Captura de tela do painel status do locatário](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Os detalhes de status do locatário incluem status do conector, integridade do serviço do Intune e notícias do Intune. Se houver algum problema com seu locatário ou o Intune em si, você encontrará detalhes no painel **status do locatário** . Para obter mais informações, consulte [status do locatário do Intune](../tenant-status.md).

12. No [Intune](https://aka.ms/intuneportal), selecione **solucionar problemas** para acessar um atalho sobre dicas de solução de problemas, solicitar suporte ou verificar o status do Intune. Essas informações são específicas do usuário do Intune que você selecionar.

    ![Captura de tela do painel de solução de problemas](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Para obter mais informações sobre solução de problemas no Intune, consulte [usar o portal de solução de problemas para ajudar os usuários em sua empresa](../help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Configurar o portal do Azure

O Azure permite que você personalize e configure a exibição do Portal.

### <a name="change-the-sidebar"></a>Alterar a barra lateral

A **barra lateral** no lado esquerdo do portal do Azure mostra-lhe uma lista de todos os serviços do Azure disponíveis. A vista predefinida desta lista abrangente pode ser alterada para que mantenha uma vista persistente dos serviços mais relevantes para si. As informações abaixo utilizam o Intune como o exemplo de um serviço a adicionar ao topo da lista.

![Um utilizador a procurar o Microsoft Intune na lista "Mais serviços".](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. Selecione **Todos os serviços** na barra lateral no lado esquerdo da página.
2. Procure **Intune** na caixa de filtragem.
3. Selecione a **estrela** para adicionar o Intune à parte inferior da lista dos seus serviços preferidos.
4. Paire o cursor sobre o serviço Intune. Selecione e arraste o Intune através dos **três pontos verticais** à direita do nome do serviço.

### <a name="change-the-dashboard"></a>Alterar o painel

A sua página de destino predefinida é o **dashboard**. Esta é a página onde personaliza os seus mosaicos para apresentar as informações que lhe são mais relevantes.

![Um imagem do novo dashboard genérico. Apresenta a barra lateral com todos os serviços à esquerda e o dashboard principal ao centro. Os botões de modificação do dashboard encontram-se na parte superior, com mosaicos que disponibilizam o acesso a todos os recursos, tutoriais de início rápido, o estado de funcionamento do serviço e o Azure Marketplace.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

Para modificar o seu dashboard atual, selecione o botão **Editar dashboard**. Se não quiser alterar o seu dashboard predefinido, também pode criar um **Novo dashboard**. Criar um novo dashboard disponibiliza-lhe um dashboard vazio e privado com a **Galeria de Mosaicos**, que lhe permite adicionar ou reordenar mosaicos. Pode encontrar mosaicos através da categoria **Geral**, do **Tipo**, da funcionalidade **Procurar** ou através de um **Grupo de recursos** ou **Etiqueta**.

Também pode adicionar mosaicos diretamente ao seu dashboard a partir de qualquer botão de **reticências** e ao selecionar **Afixar ao dashboard**.

![Um grande plano da localização Utilizadores e Grupos > Todos os grupos no Intune, com a opção "Afixar ao dashboard" visível na extremidade direita de um grupo.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

Esta funcionalidade ser-lhe-á mais relevante após adicionar mais conteúdos, tais como grupos e utilizadores, ao Intune.

## <a name="next-steps"></a>Próximos passos

Para ser executado rapidamente em Microsoft Intune, percorra os guias de início rápido do Intune primeiro Configurando uma conta gratuita do Intune.

> [!div class="nextstepaction"]
> [Início rápido: Experimente o Microsoft Intune gratuitamente](free-trial-sign-up.md)
