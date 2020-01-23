---
title: Início Rápido – experimentar gratuitamente o Microsoft Intune
titleSuffix: ''
description: Neste início rápido, criará uma subscrição de avaliação gratuita, terá conhecimento das configurações suportadas e dos requisitos de rede e configurará opcionalmente o seu nome de domínio.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/16/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1baf0b4273a9074ac7172c08240a8e3c3a9d7fa
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541120"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Início Rápido: experimentar gratuitamente o Microsoft Intune

O Microsoft Intune ajuda-o a proteger os dados empresariais da sua força de trabalho através da gestão de dispositivos e aplicações. Neste início rápido, criará uma subscrição gratuita para experimentar o Intune num ambiente de teste.

O Intune fornece MDM (gerenciamento de dispositivo móvel) e MAM (gerenciamento de aplicativo móvel) de um serviço seguro baseado em nuvem que é administrado usando o centro de administração do Microsoft Endpoint Manager. A utilização do Intune permite assegurar que os recursos empresariais da sua força de trabalho (dados, dispositivos e aplicações) são configurados, acedidos e atualizados corretamente de forma a cumprir os requisitos e as políticas de conformidade da sua empresa.

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

- [Browsers e sistemas operativos suportados](supported-devices-browsers.md)
- [Largura de banda e requisitos de configuração de rede](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode **inscrever-se** numa conta nova e utilizar o Intune para a sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

1. Aceda à página da [Avaliação do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) e preencha o formulário.

    ![Captura de ecrã da página Web de inscrição numa conta de Avaliação do Microsoft Intune](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    Se a maioria das suas operações de TI e dos seus utilizadores estiverem numa região diferente da sua, é recomendado que selecione essa região em **País ou região**. O Azure utiliza as suas informações regionais para prestar os serviços corretos. Não é possível alterar esta definição posteriormente.

2. Utilize o nome da sua empresa seguido de **.onmicrosoft.com** para criar uma conta. 

    ![Captura de tela do novo processo de credencial da conta de avaliação do Intune](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    Se sua organização tiver seu próprio domínio personalizado que você deseja usar sem **. onmicrosoft.com**, você poderá alterar isso no centro de administração Microsoft 365 descrito mais adiante neste artigo.

3. Pode ver as novas informações da sua conta nova no final do processo de inscrição.

    ![Imagem das informações da conta](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Entrar no Intune no Microsoft Endpoint Manager

Se você ainda não tiver entrado no portal, conclua as seguintes etapas:

1. Abra uma nova janela do browser e introduza **https://devicemanagement.microsoft.com** na barra de endereço. 
2. Use a ID de usuário que você recebeu nas etapas acima para entrar ( *yourID@yourdomain* . onmicrosoft.com).

    ![Imagem da página de entrada do portal](./media/free-trial-sign-up/azure-portal-signin.png)

Quando se inscrever numa versão de avaliação, também receberá uma mensagem de e-mail com as informações da sua conta no endereço de e-mail que indicou durante o processo de inscrição. Este e-mail confirma que a sua versão de avaliação está ativa.

> [!TIP]
> Ao trabalhar com o Microsoft Endpoint Manager, você pode ter resultados melhores trabalhando com um navegador em modo normal, em vez de modo privado.

## <a name="confirm-the-mdm-authority-in-intune"></a>Confirmar a autoridade de MDM no Intune

Por padrão, a autoridade de MDM é definida quando você cria sua avaliação gratuita. Você pode confirmar se a autoridade de MDM está definida usando as seguintes etapas:

1. Se você ainda não tiver entrado, entre no Microsoft Endpoint Manager.
2. Clique em **Administração de locatário**.
3. Exiba os detalhes do locatário. A **autoridade de MDM** deve ser definida como **Microsoft Intune**.

Se, depois de entrar no Microsoft Endpoint Manager, você vir uma faixa laranja indicando que ainda não definiu a autoridade de MDM, você poderá ativá-la no momento. A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Tem de definir uma autoridade de MDM para que os utilizadores possam inscrever dispositivos para gestão.

### <a name="to-set-the-mdm-authority-to-intune-follow-these-steps"></a>Para definir a autoridade de MDM para o Intune, siga estas etapas:

1. Abra uma nova janela do browser e introduza **https://portal.azure.com** na barra de endereço. 
2. Selecione **Todos os serviços** > **Microsoft Intune**.
3. Selecione a faixa que indica que não ativou a gestão de dispositivos ou, se não vir imediatamente a faixa, selecione **Inscrição de dispositivos**. O painel **Escolher Autoridade de MDM** será apresentado, se ainda não tiver ativado a gestão de dispositivos.

    > [!NOTE]
    > Se você tiver definido a autoridade de MDM, verá o valor da autoridade de MDM na folha **registro do dispositivo** . A faixa cor de laranja só é apresentada se ainda não tiver configurado a autoridade de MDM. 

    ![Imagem do painel Escolher Autoridade de MDM](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. Se sua autoridade de MDM não estiver definida, em **escolher autoridade de MDM**, defina sua autoridade de MDM como **autoridade de MDM do Intune**.

Para obter mais informações sobre a autoridade de MDM, veja [Definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md).

## <a name="configure-your-custom-domain-name-optional"></a>Configurar o nome de domínio personalizado (opcional)

Conforme mencionado acima, se sua organização tiver seu próprio domínio personalizado que você deseja usar sem **. onmicrosoft.com**, você poderá alterá-lo no centro de administração do Microsoft 365. Você pode adicionar, verificar e configurar seu nome de domínio personalizado usando as etapas a seguir.  

> [!IMPORTANT]
> Você não pode renomear ou remover a parte **onmicrosoft.com** *inicial* do nome de domínio. No entanto, você pode adicionar, verificar ou remover nomes de domínio *personalizados* usados com o Intune para manter sua identidade de negócios clara. Para obter mais informações, consulte [configurar um nome de domínio personalizado](custom-domain-name-configure.md).

1. Vá para [Microsoft 365 centro de administração](https://admin.microsoft.com) e entre usando sua conta de administrador.

2. No painel de navegação, selecione **Configuração** > **Domínios** > **Adicionar domínio**.

3. Escreva o seu nome de domínio personalizado. Depois, selecione **Seguinte**.

   ![Captura de tela do centro de administração Microsoft 365-Adicionar domínio](./media/free-trial-sign-up/domain-custom-add.png)

4. Verifique se você é o proprietário do domínio que você inseriu na etapa anterior. 
    
    A seleção de **enviar código por e-mail** fará com que seja enviado um e-mail para o contacto registado do seu domínio. Depois de receber o e-mail, copie o código e introduza-o no campo **Escreva o seu código de verificação aqui**. Se o código de verificação corresponder, o domínio será adicionado ao seu inquilino. O e-mail apresentado poderá não parecer familiar. Alguns registradores ocultam o endereço de email real. Além disso, o endereço de email pode ser diferente e o que foi fornecido quando o domínio foi registrado.

   ![Captura de tela de Microsoft 365 centro de administração-verificar domínio](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > Para obter mais informações sobre a verificação de registo TXT, veja [Criar registos DNS em qualquer fornecedor de alojamento DNS para o Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Experiências de administrador

Há dois portais que serão usados com mais frequência:
- O centro de administração do Microsoft Endpoint Manager ([https://devicemanagement.microsoft.com/](https://devicemanagement.microsoft.com/)) é onde você pode explorar os [recursos do Intune](what-is-intune.md). É aí que um administrador funcionaria com o Intune.
- O[https://admin.microsoft.com](https://admin.microsoft.com)(centro de administração do Microsoft 365) é onde você pode adicionar e gerenciar usuários, se não estiver usando Azure Active Directory para isso. Também pode gerir outros aspetos da sua conta, incluindo faturação e suporte.

## <a name="next-steps"></a>Próximos passos

Neste guia de início rápido, criou uma subscrição gratuita para experimentar o Intune num ambiente de teste. Para obter mais informações sobre como configurar o Intune, veja [Configurar o Intune](setup-steps.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Guia de Início Rápido: criar um utilizador e atribuir uma licença ao mesmo](quickstart-create-user.md)
