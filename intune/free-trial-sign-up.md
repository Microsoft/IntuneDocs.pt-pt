---
title: Início Rápido – experimentar gratuitamente o Microsoft Intune
titlesuffix: ''
description: Neste início rápido, criará uma subscrição de avaliação gratuita, terá conhecimento das configurações suportadas e dos requisitos de rede e configurará opcionalmente o seu nome de domínio.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2257253d023c97d14418b3566c0c493a3cd8f615
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737921"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Início rápido: Experimente gratuitamente o Microsoft Intune 

O Microsoft Intune ajuda-o a proteger os dados empresariais da sua força de trabalho através da gestão de dispositivos e aplicações. Neste início rápido, criará uma subscrição gratuita para experimentar o Intune num ambiente de teste.

O Intune fornece gestão de dispositivos móveis (MDM) e gestão de aplicações móveis (MAM) a partir de um serviço seguro baseado na cloud que é administrado com recurso ao portal do Microsoft Azure. A utilização do Intune permite assegurar que os recursos empresariais da sua força de trabalho (dados, dispositivos e aplicações) são configurados, acedidos e atualizados corretamente de forma a cumprir os requisitos e as políticas de conformidade da sua empresa. 

## <a name="prerequisites"></a>Pré-requisitos
Antes de configurar o Microsoft Intune, reveja os seguintes requisitos:

   - [Browsers e sistemas operativos suportados](supported-devices-browsers.md) 
   - [Largura de banda e requisitos de configuração de rede](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Inscreva-se numa avaliação gratuita do Microsoft Intune

Pode experimentar o Intune de forma gratuita durante 30 dias. Se já tiver uma conta escolar ou profissional, **inicie sessão** com a mesma e adicione o Intune à sua subscrição. Caso contrário, pode **inscrever-se** numa conta nova e utilizar o Intune para a sua organização.

> [!IMPORTANT]
> Não pode combinar uma conta escolar ou profissional existente após inscrever-se numa conta nova.

1. Aceda à página da [Avaliação do Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) e preencha o formulário.

    ![Captura de ecrã da página Web de inscrição numa conta de Avaliação do Microsoft Intune](./media/account-sign-up-site-full-browser.png)

    Se a maioria das suas operações de TI e dos seus utilizadores estiverem numa região diferente da sua, é recomendado que selecione essa região em **País ou região**. O Azure utiliza as suas informações regionais para prestar os serviços corretos. Não é possível alterar esta definição posteriormente.

2. Utilize o nome da sua empresa seguido de **.onmicrosoft.com** para criar uma conta. 

    ![Captura de ecrã do processo de credencial versão de avaliação do Microsoft Intune conta nova](./media/account-sign-up-site-user-id.png)

    Se quiser utilizar o domínio personalizado próprio da sua organização sem **.onmicrosoft.com**, pode alterar isso no Portal de Administração do Office 365 descrito abaixo neste artigo.

3. Pode ver as novas informações da sua conta nova no final do processo de inscrição.

    ![Imagem das informações da conta](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Iniciar sessão no portal do Azure

1. Abra uma nova janela do browser e introduza **https://portal.azure.com** na barra de endereço. 
2. Utilize as credenciais que lhe foram fornecidas nos passos acima para iniciar sessão.

    ![Imagem da página de início de sessão do portal do Azure](./media/azure-portal-signin.png)

3. Para ver o Microsoft Intune no portal do Azure, selecione **Todos os serviços** na barra lateral, no lado esquerdo da página.
4. Procure **Microsoft Intune** na caixa do filtro e selecione-o.
5. Selecione a **estrela** para adicionar o Intune à parte inferior da lista dos seus serviços preferidos e abra o dashboard do Intune.

Quando se inscrever numa versão de avaliação, também receberá uma mensagem de e-mail com as informações da sua conta no endereço de e-mail que indicou durante o processo de inscrição. Este e-mail confirma que a sua versão de avaliação está ativa.

> [!TIP]
> Ao trabalhar com o portal do Azure, poderá obter melhores resultados se utilizar um browser no modo normal, em vez de no modo privado.

## <a name="set-the-mdm-authority-to-intune"></a>Definir a autoridade de MDM como o Intune

Depois de iniciar sessão no portal do Azure e selecionar o Intune, poderá ver uma faixa cor de laranja a indicar que ainda não definiu a autoridade de MDM. A definição da autoridade de gestão de dispositivos móveis (MDM) determina como gere os seus dispositivos. Tem de definir uma autoridade de MDM para que os utilizadores possam inscrever dispositivos para gestão.

Para definir a autoridade de MDM como o Intune, siga estes passos.

1. Abra uma nova janela do browser e introduza **https://portal.azure.com** na barra de endereço. 
2. Selecione **Todos os serviços** > **Microsoft Intune**.
3. Selecione a faixa que indica que não ativou a gestão de dispositivos ou, se não vir imediatamente a faixa, selecione **Inscrição de dispositivos**. O painel **Escolher Autoridade de MDM** será apresentado, se ainda não tiver ativado a gestão de dispositivos.

    > [!NOTE]
    > A faixa cor de laranja só é apresentada se ainda não tiver configurado a autoridade de MDM.

    ![Imagem do painel Escolher Autoridade de MDM](./media/choose-mdm-authority.png) 

4. Em **Escolher Autoridade de MDM**, defina a sua autoridade de MDM como **Autoridade de MDM do Intune**.

Para obter mais informações sobre a autoridade de MDM, veja [Definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md).

## <a name="configure-your-custom-domain-name-optional"></a>Configurar o nome de domínio personalizado (opcional)

Conforme mencionado acima, se quiser utilizar o domínio personalizado próprio da sua organização sem **.onmicrosoft.com**, pode alterar isso no Portal de Administração do Office 365. Vai adicionar, verificar e configurar o seu nome de domínio personalizado.  

> [!IMPORTANT]
> Não é possível mudar o nome ou remover a parte **onmicrosoft.com** do nome de domínio inicial. Pode adicionar, verificar ou remover nomes de domínio personalizados utilizados com o Intune para manter a identidade da sua empresa clara.

1. Aceda ao [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) e inicie sessão através da sua conta de administrador.

2. No painel de navegação, selecione **Configuração** > **Domínios** > **Adicionar domínio**.

3. Escreva o seu nome de domínio personalizado. Depois, selecione **Seguinte**.

   ![Captura de ecrã do Centro de administração do Office 365 – Adicionar domínio](./media/domain-custom-add.png)

4. Verifique se é o proprietário do domínio que introduziu no passo anterior. 
    
    A seleção de **enviar código por e-mail** fará com que seja enviado um e-mail para o contacto registado do seu domínio. Depois de receber o e-mail, copie o código e introduza-o no campo **Escreva o seu código de verificação aqui**. Se o código de verificação corresponder, o domínio será adicionado ao seu inquilino. O e-mail apresentado poderá não parecer familiar. Algumas entidades de registo de domínio ocultam o endereço de e-mail real que foi fornecido quando o domínio foi registado.

   ![Captura de ecrã do Centro de administração do Office 365 - verificar domínio](./media/domain-custom-verify.png)

   > [!NOTE]
   > Para obter mais informações sobre a verificação de registo TXT, veja [Criar registos DNS em qualquer fornecedor de alojamento DNS para o Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Experiências de administrador

Existem dois portais que pode utilizar:
- O dashboard do Intune no Azure ([portal.azure.com](https://portal.azure.com)) é o local onde poderá explorar as [funcionalidades do Intune](what-is-intune.md). Normalmente, irá realizar o seu trabalho no dashboard do Intune.
- O Centro de Administração do Office 365 ([portal.office.com](https://portal.office.com)) é o local onde poderá adicionar e gerir utilizadores se não estiver a utilizar o Azure Active Directory para o fazer. Também pode gerir outros aspetos da sua conta, incluindo faturação e suporte.

## <a name="next-steps"></a>Passos Seguintes

Neste guia de início rápido, criou uma subscrição gratuita para experimentar o Intune num ambiente de teste. Para obter mais informações sobre como configurar o Intune, veja [Configurar o Intune](setup-steps.md).

Para seguir esta série de guias de início rápido do Intune, continue para o próximo guia de início rápido.

> [!div class="nextstepaction"]
> [Início rápido: Criar um utilizador e atribuir uma licença ao mesmo](quickstart-create-user.md)
