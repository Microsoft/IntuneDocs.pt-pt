---
title: Tutorial – Guia de instruções do Intune no Microsoft Endpoint Manager
titleSuffix: Microsoft Intune
description: Neste tutorial, você fará um tour Microsoft Intune no centro de administração do Microsoft Endpoint Manager para entender melhor como realizar tarefas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267f09c3dc16aab10fbe64f0e8662ee6f7c7ffa0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/07/2019
ms.locfileid: "74908226"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Tutorial: guia de instruções do Intune no Microsoft Endpoint Manager

O [Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contém mais de 100 serviços para ajudá-lo com uma variedade de cenários e possibilidades de computação em nuvem. Microsoft Intune é um dos vários serviços disponíveis no Azure. O Intune ajuda a garantir que os dispositivos, aplicativos e dados da sua empresa atendam aos requisitos de segurança da sua empresa. Você tem o controle para definir quais requisitos precisam ser verificados e o que acontece quando esses requisitos não são atendidos. O [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) é onde você pode encontrar o serviço Microsoft Intune, bem como outras configurações relacionadas ao gerenciamento de dispositivos. A compreensão dos recursos disponíveis no Intune ajudará você a realizar várias tarefas de MDM (gerenciamento de dispositivo móvel) e MAM (gerenciamento de aplicativo móvel).

> [!NOTE]
> O Microsoft Endpoint Manager é uma plataforma de gerenciamento de ponto de extremidade única e integrada para gerenciar todos os seus pontos de extremidade. Este centro de administração do Microsoft Endpoint Manager integra o ConfigMgr e o Microsoft Intune.

Neste tutorial, irá:
> [!div class="checklist"]
> * Tour pelo centro de administração do Microsoft Endpoint Manager
> * Personalizar sua exibição do centro de administração do Microsoft Endpoint Manager

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Browsers e sistemas operativos suportados](../supported-devices-browsers.md) 
- [Largura de banda e requisitos de configuração de rede](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, você pode [se inscrever para uma conta de avaliação gratuita](free-trial-sign-up.md) para usar o Intune para sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Microsoft Intune de Tour no centro de administração do Microsoft Endpoint Manager

Siga as etapas abaixo para entender melhor o Intune no centro de administração do Microsoft Endpoint Manager. Depois de concluir o Tour, você terá uma compreensão melhor de algumas das principais áreas do Intune.

1. Abra um navegador e entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Se você for novo no Intune, use sua assinatura de avaliação gratuita.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-Home Page](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Quando você abre o Microsoft Endpoint Manager ou qualquer outro serviço no Azure, o serviço é exibido em um painel. Algumas das primeiras cargas de trabalho que você pode usar no Intune incluem **dispositivos**, **aplicativos**, **usuários**e **grupos**. Uma carga de trabalho é simplesmente uma subárea de um serviço. Quando você seleciona a carga de trabalho, ela abre esse painel como uma página inteira. Outros painéis deslizam do lado direito do painel quando são abertos e fecham para revelar o painel anterior. 

    Por padrão, ao abrir o Microsoft Endpoint Manager, você verá o painel **página inicial** . Esse painel fornece um instantâneo Visual geral do status do locatário e do status de conformidade, bem como outros links úteis relacionados.

2. No painel de navegação, selecione **painel** para exibir detalhes gerais sobre os dispositivos e aplicativos cliente em seu locatário do Intune. Se você estiver começando com um novo locatário do Intune, ainda não terá nenhum dispositivo registrado. 

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-painel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    O Intune permite que você gerencie os dispositivos e aplicativos da sua força de funcionários, incluindo como eles acessam os dados da empresa. Para usar esse serviço de MDM (gerenciamento de dispositivo móvel), os dispositivos devem primeiro ser registrados no Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune. 

    Há vários métodos para registrar os dispositivos da sua força de funcionários no Intune. Cada método depende da propriedade do dispositivo (pessoal ou empresarial), do tipo de dispositivo (iOS, Windows, Android) e dos requisitos de gestão (reposições, afinidade, bloqueio). No entanto, antes de poder habilitar o registro do dispositivo, você deve configurar sua infraestrutura do Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md). Para obter mais informações sobre como preparar seu ambiente do Intune (locatário), consulte [Configurar o Intune](setup-steps.md). Quando o seu locatário do Intune estiver pronto, você poderá registrar dispositivos. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](../enrollment/device-enrollment.md)

3. No painel de navegação, selecione **dispositivos** para exibir detalhes sobre os dispositivos registrados no seu locatário do Intune. 

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **dispositivos**.

    O painel **dispositivos-visão geral** tem várias guias que permitem exibir um resumo dos seguintes status e alertas:
    - **Status do registro** -examine os detalhes sobre os dispositivos registrados no Intune por falhas de plataforma e registro.
    - **Alertas de registro** -encontre mais detalhes sobre os dispositivos não atribuídos por plataforma. 
    - **Status de conformidade** -examine o status de conformidade com base no dispositivo, política, configuração, ameaças e proteção. Além disso, esse painel fornece uma lista de dispositivos sem uma política de conformidade.
    - **Status de configuração** -examine o status de configuração dos perfis de dispositivo, bem como a implantação de perfil. e 
    - **Status de atualização de software** – consulte um visual do status de implantação para todos os dispositivos e para todos os usuários.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. No painel **dispositivos – visão geral** , selecione **políticas de conformidade** para exibir detalhes sobre a conformidade de dispositivos gerenciados pelo Intune. Você verá detalhes semelhantes à imagem a seguir.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-políticas de conformidade](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **conformidade do dispositivo**.

    Os requisitos de conformidade são essencialmente regras, como exigir um PIN de dispositivo ou exigir criptografia de dispositivo. As políticas de conformidade do dispositivo definem as regras e configurações que um dispositivo deve seguir para ser considerado em conformidade. Para usar a conformidade do dispositivo, você deve ter:
    - Um Intune e uma assinatura do Azure Active Directory (Azure AD) Premium
    - Dispositivos que executam uma plataforma com suporte
    - Os dispositivos devem ser registrados no Intune
    - Dispositivos registrados em um usuário ou nenhum usuário primário.
    
    Para obter mais informações, consulte Introdução [às políticas de conformidade do dispositivo no Intune](../protect/device-compliance-get-started.md).

5. No painel **dispositivos – visão geral** , selecione **acesso condicional** para exibir detalhes sobre as políticas de acesso.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-acesso condicional](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **acesso condicional**.

    O acesso condicional refere-se a maneiras que você pode controlar os dispositivos e aplicativos que têm permissão para se conectar ao seu email e aos recursos da empresa. Para saber mais sobre o acesso condicional baseado em dispositivo e com base no aplicativo, e encontrar cenários comuns para usar o acesso condicional com o Intune, consulte [o que é o acesso condicional?](../protect/conditional-access.md)

6. No painel de navegação, selecione **dispositivos** > **perfis de configuração** para exibir detalhes sobre perfis de dispositivo no Intune.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-perfis de configuração](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **configuração do dispositivo**.

    O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Você pode criar perfis para diferentes dispositivos e plataformas diferentes, incluindo iOS, Android, macOS e Windows. Em seguida, você pode usar o Intune para aplicar o perfil aos dispositivos em sua organização.   

    Para obter mais informações sobre a configuração do dispositivo, consulte [aplicar configurações de recursos em seus dispositivos usando perfis de dispositivo no Microsoft Intune](../configuration/device-profiles.md).

7. No painel de navegação, selecione **dispositivos** > **todos os dispositivos** exibam detalhes sobre os dispositivos registrados do seu locatário do Intune. Se você estiver começando com uma nova inscrição do Intune, ainda não terá nenhum dispositivo registrado.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-todos os dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Esta lista de dispositivos mostra os principais detalhes sobre conformidade, a versão do sistema operacional e a data do último check-in.

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **dispositivos** > **todos os dispositivos**.
 
8. No painel de navegação, selecione **aplicativos** para exibir uma visão geral do status do aplicativo. Esse painel fornece o status de instalação do aplicativo com base nas seguintes guias:

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **aplicativos cliente**.

    O painel **aplicativos-visão geral** tem duas guias que permitem exibir um resumo dos seguintes status:
    - **Status da instalação** -exiba as principais falhas de instalação por dispositivo, bem como os aplicativos com falhas de instalação.  
    - **Status da política de proteção de aplicativo** -encontre detalhes sobre usuários atribuídos às políticas de proteção do aplicativo, bem como usuários sinalizados.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-aplicativos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune. O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha. 

    > [!NOTE]
    > O painel **aplicativos – visão geral** também fornece o status do locatário e os detalhes da conta.

    Para obter mais informações sobre como adicionar e atribuir aplicativos, consulte [Add apps to Microsoft Intune](../apps/apps-add.md) and [assign apps to groups with Microsoft Intune](../apps/apps-deploy.md).

9. No painel **aplicativos – visão geral** , selecione **todos os aplicativos** para ver uma lista de aplicativos que foram adicionados ao Intune.

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **aplicativos cliente** > **aplicativos**.

    Você pode adicionar uma variedade de tipos de aplicativo diferentes com base na plataforma para o Intune. Depois que um aplicativo tiver sido adicionado, você poderá atribuí-lo a grupos de usuários. 

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-todos os aplicativos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](~/apps/apps-add.md). 

10. No painel de navegação, selecione **usuários** para exibir detalhes sobre os usuários que você incluiu no Intune. Esses usuários são a força de obra da sua empresa.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-usuários](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **usuários**.

    Você pode adicionar usuários diretamente ao Intune ou sincronizar usuários do seu Active Directory local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Você também pode conceder aos usuários permissões adicionais para acessar o Intune. Para obter mais informações, consulte [Adicionar usuários e conceder permissão administrativa ao Intune](users-add.md).

11. No painel de navegação, selecione **grupos** para exibir detalhes sobre os grupos de Azure Active Directory (AD do Azure) incluídos no Intune. Como administrador do Intune, você usa grupos para gerenciar dispositivos e usuários.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-grupos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **grupos**.

    Você pode configurar grupos para atender às suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, você pode definir políticas para muitos usuários ou implantar aplicativos em um conjunto de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar usuários e dispositivos](../groups-add.md).

12. No painel de navegação, selecione **Administração de locatários** para exibir detalhes sobre seu locatário do Intune.

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **status do locatário**.

    O painel de **status administrador de locatários-locatário** fornece guias para **detalhes do locatário**, **status do conector**e painel de **integridade do serviço**. Se houver algum problema com seu locatário ou o Intune em si, você encontrará detalhes disponíveis neste painel. 

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-status do locatário](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Para obter mais informações, consulte [status do locatário do Intune](../tenant-status.md).

13. No painel de navegação, selecione **solução de problemas + suporte** > **solucionar problemas** para verificar os detalhes de status em um usuário específico. 

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **solucionar problemas**.

    Na lista suspensa **atribuições** , você pode optar por exibir as atribuições de destino de aplicativos cliente, políticas, anéis de atualização e restrições de registro. Além disso, esse painel fornece detalhes do dispositivo, status de proteção do aplicativo e falhas de registro para um usuário específico.

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-solucionar problemas](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Para obter mais informações sobre solução de problemas no Intune, consulte [usar o portal de solução de problemas para ajudar os usuários em sua empresa](../help-desk-operators.md).

14. No painel de navegação, selecione **solução de problemas + suporte** > **ajuda e suporte** para solicitar ajuda. 

    > [!TIP]
    > Se você já usou o Intune no portal do Azure, encontrou os detalhes acima na portal do Azure entrando no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **ajuda e suporte**.

    Como administrador de ti, você pode usar a opção **ajuda e suporte** para pesquisar e exibir soluções, bem como o arquivo de um tíquete de suporte online para o Intune. 

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager-ajuda e suporte](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Para criar um tíquete de suporte, sua conta deve ser atribuída como uma função de administrador no Azure Active Directory. As funções de administrador incluem, **administrador do Intune**, **administrador global**e **administrador de serviços**. 

    Para obter mais informações, consulte [como obter suporte para Microsoft Intune](../get-support.md).

15. No painel de navegação, selecione **solução de problemas + suporte** > **cenários guiados** para exibir os cenários guiados do Intune disponíveis. 

    Um cenário guiado é uma série personalizada de etapas centradas em um caso de uso de ponta a ponta. Cenários comuns são baseados na função que um administrador, um usuário ou um dispositivo desempenha em sua organização. Essas funções normalmente exigem uma coleção de perfis, configurações, aplicativos e controles de segurança com cuidado, para fornecer a melhor experiência de usuário e segurança.

    Se você não estiver familiarizado com todas as etapas e os recursos necessários para implementar um cenário específico do Intune, cenários orientados podem ser usados como ponto de partida. 

    ![Captura de tela do centro de administração do Microsoft Endpoint Manager – cenários guiados](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Para obter mais informações sobre cenários guiados, consulte [visão geral de cenários guiados](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Configurar o centro de administração do Microsoft Endpoint Manager

O Azure permite que você personalize e configure a exibição do Portal.

### <a name="change-the-dashboard"></a>Alterar o painel

O **painel** para exibir detalhes gerais sobre os dispositivos e aplicativos cliente no seu locatário do Intune. Os painéis fornecem uma maneira de criar uma exibição focalizada e organizada no centro de administração do Microsoft Endpoint Manager. Use painéis como um espaço de trabalho onde você pode iniciar tarefas rapidamente para operações diárias e monitorar recursos. Crie painéis personalizados com base em projetos, tarefas ou funções de usuário, por exemplo. O centro de administração do Microsoft Endpoint Manager fornece um painel padrão como um ponto de partida. Você pode editar o painel padrão, criar e personalizar painéis adicionais e publicar e compartilhar painéis para torná-los disponíveis para outros usuários. 

   ![Captura de tela do centro de administração do Microsoft Endpoint Manager-painel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Para modificar o painel atual, selecione **Editar**. Se não quiser alterar o seu dashboard predefinido, também pode criar um **Novo dashboard**. Criar um novo dashboard disponibiliza-lhe um dashboard vazio e privado com a **Galeria de Mosaicos**, que lhe permite adicionar ou reordenar mosaicos. Você pode encontrar blocos por categoria ou tipo de recurso. Você também pode pesquisar blocos específicos. Selecione **meu painel** para selecionar qualquer um dos painéis personalizados existentes.

### <a name="change-the-portal-settings"></a>Alterar as configurações do portal

Você pode personalizar o centro de administração do Microsoft Endpoint Manager escolhendo a exibição padrão, o tema, o período de tempo limite de credenciais, bem como as configurações de idioma e região.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Próximos passos

Para ser executado rapidamente em Microsoft Intune, percorra os guias de início rápido do Intune primeiro Configurando uma conta gratuita do Intune.

> [!div class="nextstepaction"]
> [Início rápido: Experimente o Microsoft Intune gratuitamente](free-trial-sign-up.md)
