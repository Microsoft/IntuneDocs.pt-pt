---
title: Tutorial - instruções Intune no portal do Azure
titleSuffix: Microsoft Intune
description: Neste tutorial, irá realizar uma visita guiada Microsoft Intune para compreender melhor como realizar tarefas.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 01/31/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c733dbbf992ae10e14ba711b34e621d3f0fb3da8
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57395271"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutorial: Passo a passo do Microsoft Intune no portal do Azure

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contém mais de 100 serviços para ajudá-lo com uma variedade de cenários de computação em nuvem e de todas as possibilidades. O Microsoft Intune é um dos vários serviços disponíveis no Azure. Intune ajuda a garantir que os dispositivos, aplicações e dados da sua empresa cumprem os requisitos de segurança de sua empresa. Tem o controle para o conjunto de requisitos precisam ser verificado e o que acontece quando esses requisitos não forem cumpridos. Pode encontrar o serviço Microsoft Intune no [portal do Azure](https://portal.azure.com). Noções básicas sobre as funcionalidades disponíveis no Intune irá ajudá-lo a realizar tarefas de gestão de dispositivos móveis (MDM) de várias e gestão de aplicações móveis (MAM).

Neste tutorial, irá:
> [!div class="checklist"]
> * Tour pelo Microsoft Intune
> * Configurar o portal do Azure

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

   - [Browsers e sistemas operativos suportados](supported-devices-browsers.md) 
   - [Largura de banda e requisitos de configuração de rede](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode [Inscreva-se uma conta de avaliação gratuita](free-trial-sign-up.md) para utilizar o Intune para a sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="tour-microsoft-intune"></a>Tour pelo Microsoft Intune

Siga os passos abaixo para compreender melhor o Intune no portal do Azure. Depois de concluir a visita guiada, terá uma melhor compreensão sobre algumas das principais áreas do Intune.

1. Abra um browser e inicie sessão para o [portal do Intune](https://aka.ms/intuneportal). Se estiver familiarizado com o Intune, utilize a sua subscrição de avaliação gratuita.

    ![Captura de ecrã do portal do Microsoft Intune](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Quando abrir o Intune ou qualquer outro serviço no Azure, o serviço é apresentado num painel. Algumas das primeiras cargas de trabalho pode utilizar no Intune inclui **dispositivos**, **aplicações de cliente**, **utilizadores**, e **grupos**. Uma carga de trabalho é simplesmente uma área de frações de um serviço. Quando seleciona a carga de trabalho, abre esse painel como uma página inteira. Outros painéis surgem a partir do lado direito do painel quando são abertos e fechar para revelam o painel anterior. Um painel também é referido como um painel. 

    Por predefinição, quando abrir o Intune irá ver a **descrição geral** painel. Este painel fornece um instantâneo visual geral do Estado de atribuição e a conformidade do dispositivo, bem como o estado de instalação de aplicações.

2. Partir [Intune](https://aka.ms/intuneportal), selecione **inscrição de dispositivos** para apresentar os detalhes sobre os dispositivos inscritos no seu inquilino do Intune. Se estiver a começar com um novo inquilino do Intune, não terá todos os dispositivos inscritos ainda. 

    ![Captura de ecrã do painel de inscrição do dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    O Intune permite-lhe gerir dispositivos de sua força de trabalho e aplicações, incluindo como aceder aos dados da sua empresa. Para utilizar este serviço de gestão (MDM) do dispositivo móvel, os dispositivos primeiro têm de estar inscritos no Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune. 

    Existem vários métodos de inscrição de dispositivos da força de trabalho para Intune. Cada método depende da propriedade do dispositivo (pessoal ou empresarial), do tipo de dispositivo (iOS, Windows, Android) e dos requisitos de gestão (reposições, afinidade, bloqueio). No entanto, antes de poder ativar a inscrição de dispositivos, tem de definir a sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md). Para obter mais informações sobre como preparar o ambiente do Intune (inquilino), consulte [configurar o Intune](setup-steps.md). Assim que tiver o seu inquilino do Intune pronto, pode inscrever dispositivos. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](device-enrollment.md)

3. Partir [Intune](https://aka.ms/intuneportal), selecione **conformidade do dispositivo** para apresentar os detalhes sobre a conformidade para dispositivos geridos pelo Intune. Verá detalhes semelhantes à imagem seguinte.

    ![Captura de ecrã do painel de conformidade do dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Requisitos de conformidade são essencialmente regras, como exigir um PIN do dispositivo ou exigir a encriptação de dispositivos. Políticas de conformidade de dispositivo definem as regras e definições que um dispositivo tem de seguir para ser considerado conforme. Para utilizar a conformidade do dispositivo, tem de ter:
    - Do Intune e uma subscrição do Azure Active Directory (Azure AD) Premium
    - Dispositivos com uma plataforma suportada
    - Dispositivos têm de estar inscritos no Intune
    - Dispositivos inscritos um utilizador ou nenhum utilizador primário.
    
    Para obter mais informações, consulte [começar a utilizar com políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

4. Partir [Intune](https://aka.ms/intuneportal), selecione **configuração do dispositivo** para apresentar os detalhes sobre os perfis de dispositivo no Intune. 

    ![Captura de ecrã do painel de configuração do dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas para "perfis de configuração". Pode criar perfis para diferentes dispositivos e plataformas diferentes, incluindo iOS, Android e Windows. Em seguida, pode utilizar o Intune para aplicar o perfil a dispositivos na sua organização.   

    Para obter mais informações sobre a configuração do dispositivo, consulte [aplicar definições de funcionalidades nos seus dispositivos com perfis de dispositivos no Microsoft Intune](device-profiles.md).

5. Partir [Intune](https://aka.ms/intuneportal), selecione **dispositivos** para apresentar os detalhes sobre o Intune o inquilino dos dispositivos inscritos. Se estiver a começar com uma nova inscrição do Intune, não terá todos os dispositivos inscritos ainda. 

    ![Captura de ecrã do painel de inscrição do dispositivo](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    O **dispositivos** painel fornece detalhes sobre o seu inquilino do dispositivos inscritos. Pode clicar em **todos os dispositivos** para apresentar uma lista de dispositivos para o seu inquilino do Intune. 

6. Partir [Intune](https://aka.ms/intuneportal), selecione **aplicações de cliente** para apresentar o estado de instalação de aplicações.

    ![Captura de ecrã do painel de aplicações de cliente](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune. O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha. Para obter mais informações sobre a adição e atribuição de aplicações, consulte [adicionar aplicações ao Microsoft Intune](apps-add.md) e [atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

7. Partir [Intune](https://aka.ms/intuneportal), selecione **acesso condicional** para apresentar os detalhes sobre as políticas de acesso.

    ![Captura de ecrã do painel de acesso condicional](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    O acesso condicional refere-se às formas como pode controlar os dispositivos e aplicações que têm permissão para se ligarem ao seu e-mail e recursos da empresa. Para saber mais sobre o acesso condicional com base no dispositivo e baseado na aplicação e descubra cenários comuns para utilizar o acesso condicional com o Intune, veja [o que é o acesso condicional?](conditional-access.md)

8. Partir [Intune](https://aka.ms/intuneportal), selecione **utilizadores** para apresentar os detalhes sobre os utilizadores que tenha incluído no Intune. Esses usuários são força de trabalho da sua empresa. 
 
    ![Captura de ecrã do painel de utilizadores](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Pode adicionar utilizadores diretamente para o Intune ou sincronizar utilizadores do Active Directory no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode dar aos utilizadores permissões adicionais para aceder ao Intune. Para obter mais informações, consulte [adicionar utilizadores e conceder permissões administrativas no Intune](users-add.md).

9. Partir [Intune](https://aka.ms/intuneportal), selecione **grupos** para apresentar os detalhes sobre os grupos do Azure Active Directory (Azure AD) incluídos no Intune. Como administrador do Intune, pode utilizar o grupo para gerir dispositivos e utilizadores. 

    ![Captura de ecrã do painel de grupos](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Pode configurar grupos para se adequar às necessidades da sua organização. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para muitos usuários ou implementar aplicações num conjunto de dispositivos. Para obter mais informações sobre os grupos, consulte [adicionar grupos para organizar utilizadores e dispositivos](groups-add.md).

10. Partir [Intune](https://aka.ms/intuneportal), selecione **ajuda e suporte** para a ajuda do pedido. Administrador de TI, pode utilizar o **ajuda e suporte** opção para procurar e ver soluções, bem como enviar um pedido de suporte online para o Intune. 

    ![Captura de ecrã do painel de ajuda e suporte](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Para criar um pedido de suporte, a conta tem de ser atribuída como uma função de administrador no Azure Active Directory. Funções de administrador incluem, **administrador do Intune**, **Administrador Global**, e **administrador de serviços**. Para obter mais informações, consulte [como obter suporte para o Microsoft Intune](get-support.md).

11. Partir [Intune](https://aka.ms/intuneportal), selecione **estado do inquilino** para apresentar os detalhes sobre o seu inquilino do Intune.

    ![Captura de ecrã do painel de estado do inquilino](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Detalhes de estado do inquilino incluem o estado do conector, o estado de funcionamento do serviço Intune e notícias do Intune. Se existirem quaisquer problemas com o seu inquilino ou o Intune em si, encontrará detalhes no **estado do inquilino** painel. Para obter mais informações, consulte [estado do inquilino do Intune](tenant-status.md).

12. Partir [Intune](https://aka.ms/intuneportal), selecione **resolução de problemas** para chegar a um atalho nas dicas de solução de problemas, pedir suporte ou verificar o estado do Intune. Estas informações são específicas do utilizador do Intune que selecionar.

    ![Captura de ecrã do painel de resolução de problemas](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Para obter mais informações sobre resolução de problemas no Intune, consulte [utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa](help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Configurar o portal do Azure

Azure permite-lhe personalizar e configurar a vista do portal.

### <a name="change-the-sidebar"></a>Alterar a barra lateral

A **barra lateral** no lado esquerdo do portal do Azure mostra-lhe uma lista de todos os serviços do Azure disponíveis. A vista predefinida desta lista abrangente pode ser alterada para que mantenha uma vista persistente dos serviços mais relevantes para si. As informações abaixo utilizam o Intune como o exemplo de um serviço a adicionar ao topo da lista.

![Um utilizador a procurar o Microsoft Intune na lista "Mais serviços".](./media/azure-add-intune1.png)

1. Selecione **Todos os serviços** na barra lateral no lado esquerdo da página.
2. Procure **Intune** na caixa de filtragem.
3. Selecione a **estrela** para adicionar o Intune à parte inferior da lista dos seus serviços preferidos.
4. Paire o cursor sobre o serviço Intune. Selecione e arraste o Intune através dos **três pontos verticais** à direita do nome do serviço.

### <a name="change-the-dashboard"></a>Alterar o dashboard

A sua página de destino predefinida é o **dashboard**. Esta é a página onde personaliza os seus mosaicos para apresentar as informações que lhe são mais relevantes.

![Um imagem do novo dashboard genérico. Apresenta a barra lateral com todos os serviços à esquerda e o dashboard principal ao centro. Os botões de modificação do dashboard encontram-se na parte superior, com mosaicos que disponibilizam o acesso a todos os recursos, tutoriais de início rápido, o estado de funcionamento do serviço e o Azure Marketplace.](./media/azure-default-dashboard.png)

Para modificar o seu dashboard atual, selecione o botão **Editar dashboard**. Se não quiser alterar o seu dashboard predefinido, também pode criar um **Novo dashboard**. Criar um novo dashboard disponibiliza-lhe um dashboard vazio e privado com a **Galeria de Mosaicos**, que lhe permite adicionar ou reordenar mosaicos. Pode encontrar mosaicos através da categoria **Geral**, do **Tipo**, da funcionalidade **Procurar** ou através de um **Grupo de recursos** ou **Etiqueta**.

Também pode adicionar mosaicos diretamente ao seu dashboard a partir de qualquer botão de **reticências** e ao selecionar **Afixar ao dashboard**.

![Um grande plano da localização Utilizadores e Grupos > Todos os grupos no Intune, com a opção "Afixar ao dashboard" visível na extremidade direita de um grupo.](./media/azure-pin-to-dashboard.png)

Esta funcionalidade ser-lhe-á mais relevante após adicionar mais conteúdos, tais como grupos e utilizadores, ao Intune.

## <a name="next-steps"></a>Passos Seguintes

Para obter a executar rapidamente no Microsoft Intune, siga os passos de guias de introdução do Intune ao primeiro de configurar uma conta gratuita do Intune.

> [!div class="nextstepaction"]
> [Início rápido: Experimente gratuitamente o Microsoft Intune](free-trial-sign-up.md)


