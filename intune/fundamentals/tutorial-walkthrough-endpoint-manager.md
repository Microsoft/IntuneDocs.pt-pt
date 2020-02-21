---
title: Tutorial - Walkthrough Intune no Microsoft Endpoint Manager
titleSuffix: Microsoft Intune
description: Neste tutorial, você irá visitar o Microsoft Intune no centro de administração do Microsoft Endpoint Manager para entender melhor como realizar tarefas.
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
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514086"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Tutorial: Walkthrough Intune no Microsoft Endpoint Manager

[O Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) contém mais de 100 serviços para o ajudar com uma variedade de cenários e possibilidades de computação em nuvem. O Microsoft Intune é um dos vários serviços disponíveis no Azure. Intune ajuda-o a garantir que os dispositivos, aplicações e dados da sua empresa cumprem os requisitos de segurança da sua empresa. Tem o controlo para definir quais os requisitos que precisam de ser verificados e o que acontece quando esses requisitos não são cumpridos. O centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) é onde pode encontrar o serviço Microsoft Intune, bem como outras definições relacionadas com a gestão de dispositivos. Compreender as funcionalidades disponíveis no Intune irá ajudá-lo a realizar várias tarefas de Gestão de Dispositivos Móveis (MDM) e Gestão de Aplicações Móveis (MAM).

> [!NOTE]
> O Microsoft Endpoint Manager é uma plataforma única e integrada de gestão de pontos finais para gerir todos os seus pontos finais. Este centro de administração do Microsoft Endpoint Manager integra a ConfigMgr e a Microsoft Intune.

Neste tutorial, irá:
> [!div class="checklist"]
> * Visite o centro de administração do Microsoft Endpoint Manager
> * Personalize a sua visão do centro de administração do Microsoft Endpoint Manager

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Browsers e sistemas operativos suportados](../supported-devices-browsers.md) 
- [Largura de banda e requisitos de configuração de rede](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode [inscrever-se numa conta de teste gratuita](free-trial-sign-up.md) para usar o Intune para a sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Tour Microsoft Intune no centro de administração do Microsoft Endpoint Manager

Siga os passos abaixo para entender melhor Intune no centro de administração do Microsoft Endpoint Manager. Assim que completar o tour, terá uma melhor compreensão de algumas das principais áreas de Intune.

1. Abra um navegador e inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Se é novo em Intune, use a sua subscrição de teste gratuita.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - página inicial](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Quando abre o Microsoft Endpoint Manager ou qualquer outro serviço no Azure, o serviço é apresentado num painel. Algumas das primeiras cargas de trabalho que pode utilizar em Intune incluem **Dispositivos**, **Apps,** **Utilizadores**e **Grupos.** Uma carga de trabalho é simplesmente uma sub-área de um serviço. Quando seleciona a carga de trabalho, abre-se o painel como uma página inteira. Outras vidraças deslizam para fora do lado direito do painel quando abrem, e perto para revelar o painel anterior. 

    Por predefinição, quando abrir o Microsoft Endpoint Manager, verá o painel de **página inicial.** Este painel fornece uma imagem visual geral do estado do inquilino e do estado de conformidade, bem como outras ligações relacionadas úteis.

2. A partir do painel de navegação, selecione **Dashboard** para mostrar detalhes gerais sobre os dispositivos e aplicações de clientes no seu inquilino Intune. Se você está começando com um novo inquilino Intune, você não terá nenhum dispositivo matriculado ainda. 

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Dashboard](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune permite-lhe gerir os dispositivos e aplicações da sua força de trabalho, incluindo a forma como acedem aos dados da sua empresa. Para utilizar este serviço de gestão de dispositivos móveis (MDM), os dispositivos devem ser matriculados primeiro em Intune. Quando um dispositivo é inscrito, é emitido um certificado MDM. Este certificado é utilizado para comunicar com o serviço Intune. 

    Existem vários métodos para inscrever os dispositivos da sua força de trabalho no Intune. Cada método depende da propriedade do dispositivo (pessoal ou corporativo), do tipo de dispositivo (iOS/iPadOS, Windows, Android) e dos requisitos de gestão (resets, afinidade, bloqueio). No entanto, antes de poder ativar a inscrição do dispositivo, tem de configurar a sua infraestrutura Intune. Em particular, a inscrição de dispositivos requer que [defina a autoridade de MDM](mdm-authority-set.md). Para mais informações sobre como preparar o seu ambiente Intune (inquilino), consulte [Configurar Intune](setup-steps.md). Assim que tiver o seu inquilino intune pronto, pode inscrever dispositivos. Para obter mais informações sobre a inscrição de dispositivos, veja [O que é a inscrição de dispositivos?](../enrollment/device-enrollment.md)

3. A partir do painel de navegação, selecione **Dispositivos** para mostrar detalhes sobre os dispositivos matriculados no seu inquilino Intune. 

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, [inserindo](https://go.microsoft.com/fwlink/?linkid=2090973) no Intune e selecionando **Dispositivos**.

    O **Painel dispositivos - Visão geral** tem vários separadores que lhe permitem ver um resumo dos seguintes estados e alertas:
    - **Estado de inscrição** - Rever detalhes sobre dispositivos inscritos intune por falhas de plataforma e de inscrição.
    - **Alertas** de inscrição - Encontre mais detalhes sobre dispositivos não atribuídos por plataforma. 
    - **Estado de conformidade** - Rever o estado de conformidade com base no dispositivo, política, definição, ameaças e proteção. Além disso, este painel fornece uma lista de dispositivos sem uma política de conformidade.
    - **Estado de configuração** - Rever o estado de configuração dos perfis do dispositivo, bem como a implementação do perfil., e 
    - Estado da **atualização** de software - Veja um visual do estado de implementação de todos os dispositivos e para todos os utilizadores.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. A partir do painel **de dispositivos - Visão geral,** selecione **as políticas** de conformidade para mostrar detalhes sobre a conformidade com os dispositivos geridos pela Intune. Verá detalhes semelhantes à seguinte imagem.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Políticas de conformidade](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima referidos no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando a Conformidade do **Dispositivo**.

    Os requisitos de conformidade são essencialmente regras, tais como exigir um PIN do dispositivo ou exigir encriptação do dispositivo. As políticas de conformidade do dispositivo definem as regras e definições que um dispositivo deve seguir para ser considerada conforme. Para utilizar a conformidade do dispositivo, deve ter:
    - Uma subscrição Premium intune e um Azure Ative Directory (Azure AD)
    - Dispositivos que executam uma plataforma suportada
    - Os dispositivos devem ser matriculados em Intune
    - Dispositivos que estejam matriculados num utilizador ou sem utilizador primário.
    
    Para mais informações, consulte Iniciar as políticas de [conformidade do dispositivo em Intune](../protect/device-compliance-get-started.md).

5. A partir do **painel dispositivos - Visão geral,** selecione **Acesso Condicional** para apresentar detalhes sobre as políticas de acesso.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Acesso condicional](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **Acesso Condicional**.

    O Acesso Condicional refere-se a formas de controlar os dispositivos e aplicações que podem ligar-se aos seus e-mails e recursos da empresa. Para conhecer o Acesso Condicional baseado em dispositivos e aplicativos, e encontrar cenários comuns para usar o Acesso Condicional com Intune, consulte [o What's Conditional Access?](../protect/conditional-access.md)

6. A partir do painel de navegação, selecione **Dispositivos** > Perfis de **Configuração** para mostrar detalhes sobre os perfis do dispositivo no Intune.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Perfis de configuração](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando a **configuração**do Dispositivo .

    O Intune inclui definições e funcionalidades que pode ativar ou desativar em diferentes dispositivos na sua organização. Estas definições e funcionalidades são adicionadas aos “perfis de configuração”. Pode criar perfis para diferentes dispositivos e diferentes plataformas, incluindo iOS/iPadOS, Android, macOS e Windows. Em seguida, pode usar o Intune para aplicar o perfil em dispositivos da sua organização.   

    Para obter mais informações sobre a configuração do dispositivo, consulte [as definições de funcionalidades de Aplicação nos seus dispositivos utilizando perfis de dispositivos no Microsoft Intune](../configuration/device-profiles.md).

7. A partir do painel de navegação, selecione **Dispositivos** > **Todos os dispositivos** para mostrar detalhes sobre os dispositivos matriculados do seu inquilino Intune. Se estiver a começar com um novo alistamento Intune, ainda não terá nenhum dispositivo matriculado.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Todos os dispositivos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Esta lista de dispositivos mostra detalhes-chave sobre conformidade, versão S e última data de check-in.

    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima referidos no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **Dispositivos** > **Todos os dispositivos**.
 
8. A partir do painel de navegação, selecione **Apps** para mostrar uma visão geral do estado da aplicação. Este painel fornece o estado de instalação da aplicação com base nos seguintes separadores:

    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima no portal Azure, assinando [intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **aplicações de Cliente.**

    As **Apps - Painel de visão geral** tem dois separadores que lhe permitem ver um resumo dos seguintes estatutos:
    - **Estado de instalação** - Veja as falhas de instalação superiores por dispositivo, bem como as aplicações com falhas de instalação.  
    - Estado da política de **proteção de aplicações** - Encontre detalhes sobre utilizadores atribuídos às políticas de proteção de aplicações, bem como utilizadores sinalizados.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Apps](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Enquanto administrador de TI, pode utilizar o Microsoft Intune para gerir as aplicações cliente utilizadas pela força de trabalho da sua empresa. Esta funcionalidade complementa a gestão de dispositivos e proteção de dados. Uma das prioridades de um administrador é garantir que os utilizadores finais têm acesso às aplicações que precisam para trabalhar. Além disso, pode querer atribuir e gerir aplicações em dispositivos que não estão inscritos no Intune. O Intune oferece várias funcionalidades para o ajudar a obter as aplicações de que precisa, nos dispositivos à sua escolha. 

    > [!NOTE]
    > As **Apps - Painel de visão geral** também fornece o estado do inquilino e detalhes da conta.

    Para obter mais informações sobre a adição e atribuição de apps, consulte [adicionar aplicações ao Microsoft Intune](../apps/apps-add.md) e [atribuir aplicações a grupos com](../apps/apps-deploy.md)o Microsoft Intune .

9. A partir das Apps - Painel de **visão geral,** selecione **Todas as aplicações** para ver uma lista de aplicações que foram adicionadas ao Intune.

    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima no portal Azure, assinando [intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **aplicações de clientes** > **Apps.**

    Pode adicionar uma variedade de diferentes tipos de aplicativos com base na plataforma ao Intune. Uma vez adicionada uma aplicação, pode atribuí-la a grupos de utilizadores. 

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Todas as aplicações](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Para obter mais informações, veja [Adicionar aplicações ao Microsoft Intune](~/apps/apps-add.md). 

10. A partir do painel de navegação, selecione **Utilizadores** para mostrar detalhes sobre os utilizadores que incluiu no Intune. Estes utilizadores são a força de trabalho da sua empresa.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Utilizadores](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Se já utilizou o Intune no portal Azure, encontrou os detalhes acima no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **Utilizadores**.

    Pode adicionar utilizadores diretamente ao Intune ou sincronizar os utilizadores a partir do seu Diretório Ativo no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode dar aos utilizadores permissões adicionais para aceder ao Intune. Para mais informações, consulte [Adicionar utilizadores e conceder permissão administrativa para Intune](users-add.md).

11. A partir do painel de navegação, selecione **Grupos** para mostrar detalhes sobre os grupos Azure Ative Directory (Azure AD) incluídos no Intune. Como administrador intune, utiliza grupos para gerir dispositivos e utilizadores.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Grupos](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, [inserindo](https://go.microsoft.com/fwlink/?linkid=2090973) em Intune e selecionando **Grupos**.

    Pode criar grupos de acordo com as suas necessidades organizacionais. Crie grupos para organizar utilizadores ou dispositivos por localização geográfica, departamento ou características de hardware. Utilize grupos para gerir tarefas em escala. Por exemplo, pode definir políticas para muitos utilizadores ou implementar aplicações para um conjunto de dispositivos. Para obter mais informações sobre grupos, consulte [Adicionar grupos para organizar utilizadores e dispositivos](../groups-add.md).

12. A partir do painel de navegação, selecione **a administração do Inquilino** para mostrar detalhes sobre o seu inquilino Intune.

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, assinando [intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando o estatuto de **Inquilino**.

    O **administrador do Inquilino -** Painel de estatuto de inquilino fornece separadores para detalhes do **Inquilino,** **estado de Conector**e **painel de saúde**de serviço. Se houver algum problema com o seu inquilino ou com o próprio Intune, encontrará detalhes disponíveis a partir deste painel. 

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Estatuto do inquilino](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Para mais informações, consulte [Intune Tenant Status](../tenant-status.md).

13. A partir do painel de navegação, selecione **Troubleshooting + suporte** > **Troubleshoot** para verificar os detalhes do estado num utilizador específico. 

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **Troubleshoot**.

    A partir da lista de **desistentes** de Atribuição, pode optar por ver as atribuições direcionadas de aplicações de clientes, políticas, anéis de atualização e restrições de inscrição. Além disso, este painel fornece detalhes do dispositivo, estado de proteção de aplicações e falhas de inscrição para um utilizador específico.

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Troubleshoot](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Para mais informações sobre resolução de problemas dentro do Intune, consulte Use o portal de resolução de [problemas para ajudar os utilizadores da sua empresa.](../help-desk-operators.md)

14. A partir do painel de navegação, selecione **Troubleshooting + suporte** > **Ajuda e suporte** para pedir ajuda. 

    > [!TIP]
    > Se já utilizou intune no portal Azure, encontrou os detalhes acima no portal Azure, inserindo-se no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selecionando **Ajuda e suporte.**

    Como administrador de TI, pode utilizar a opção **de Ajuda e Suporte** para pesquisar e visualizar soluções, bem como arquivar um bilhete de suporte on-line para Intune. 

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Ajuda e suporte](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Para criar um bilhete de apoio, a sua conta deve ser atribuída como administrador a desempenhar funções de administrador no Diretório Ativo azure. As funções de administrador incluem, **administrador intune,** **administrador global,** e **administrador de serviços.** 

    Para mais informações, consulte [Como obter suporte para o Microsoft Intune](../get-support.md).

15. A partir do painel de navegação, selecione **Troubleshooting + suporte** > **cenários guiados** para exibir cenários guiados intune disponíveis. 

    Um cenário guiado é uma série personalizada de passos centrados em torno de um caso de uso de ponta a ponta. Os cenários comuns baseiam-se no papel que um administrador, utilizador ou dispositivo desempenha na sua organização. Estas funções normalmente requerem uma coleção de perfis cuidadosamente orquestrados, configurações, aplicações e controlos de segurança para fornecer a melhor experiência e segurança do utilizador.

    Se não estiver familiarizado com todos os passos e recursos necessários para implementar um determinado cenário Intune, os cenários guiados podem ser usados como ponto de partida. 

    ![Screenshot do centro de administração do Microsoft Endpoint Manager - Cenários guiados](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Para obter mais informações sobre cenários guiados, consulte [cenários guiados.](~/fundamentals/guided-scenarios-overview.md)

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Configure o centro de administração do Microsoft Endpoint Manager

O Azure permite-lhe personalizar e configurar a vista do portal.

### <a name="change-the-dashboard"></a>Alterar o Dashboard

O **Dashboard** para mostrar detalhes gerais sobre os dispositivos e aplicações de clientes no seu inquilino Intune. Os dashboards fornecem uma forma de criar uma visão focada e organizada no centro de administração do Microsoft Endpoint Manager. Utilize os dashboards como um espaço de trabalho onde pode lançar rapidamente tarefas para operações diárias e monitorizar os recursos. Construir dashboards personalizados com base em projetos, tarefas ou funções de utilizador, por exemplo. O centro de administração do Microsoft Endpoint Manager fornece um dashboard padrão como ponto de partida. Pode editar o dashboard predefinido, criar e personalizar dashboards adicionais e publicar e partilhar dashboards para os disponibilizar a outros utilizadores. 

   ![Screenshot do centro de administração do Microsoft Endpoint Manager - Dashboard](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Para modificar o seu painel de instrumentos atual, **selecione Editar**. Se não quiser alterar o seu dashboard predefinido, também pode criar um **Novo dashboard**. Criar um novo dashboard disponibiliza-lhe um dashboard vazio e privado com a **Galeria de Mosaicos**, que lhe permite adicionar ou reordenar mosaicos. Pode encontrar azulejos por categoria ou tipo de recurso. Pode também pesquisar por azulejos específicos. Selecione **My Dashboard** para selecionar qualquer um dos seus dashboards personalizados existentes.

### <a name="change-the-portal-settings"></a>Alterar as definições do Portal

Pode personalizar o centro de administração do Microsoft Endpoint Manager escolhendo a visão padrão, o tema, o período de tempo de intervalo de credenciais, bem como as definições de idiomas e região.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Próximos passos

Para começar a correr rapidamente no Microsoft Intune, passe pelo Intune Quickstarts, criando primeiro uma conta Intune gratuita.

> [!div class="nextstepaction"]
> [Quickstart: Experimente o Microsoft Intune gratuitamente](free-trial-sign-up.md)
