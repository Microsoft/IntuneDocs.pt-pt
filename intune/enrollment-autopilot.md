---
title: Inscrever dispositivos através do Windows AutoPilot
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos com o Windows 10 através do Windows AutoPilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: b3c374e4ce6baeab8cc6fde3f6c45c63c48e34dd
ms.sourcegitcommit: d99def6e4ceb44f3e7ca10fe7cdd7f222cf814c8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903080"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Inscrever dispositivos Windows através do Windows AutoPilot
O Windows AutoPilot simplifica o aprovisionamento de dispositivos. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o AutoPilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos do AutoPilot, pode gerir políticas, perfis, aplicações, entre outros, após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Pré-requisitos
- [A Inscrição automática no Windows tem de estar ativada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Subscrição do Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Adicionar dispositivos

Pode adicionar dispositivos Windows AutoPilot ao importar um ficheiro CSV com as informações dos dispositivos.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.

    ![Captura de ecrã dos dispositivos Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device.png)

2. Em **Adicionar Dispositivos do Windows Autopilot**, procure um ficheiro CSV que liste os dispositivos que pretende adicionar. O ficheiro deve conter os números de série, os IDs dos produtos Windows, os hashes de hardware e os IDs dos pedidos opcionais dos dispositivos.

    ![Captura de ecrã Adicionar dispositivos Windows AutoPilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Depois de a importação ser concluída, selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Windows AutoPilot** > **Dispositivos** > **Sincronizar**. Uma mensagem indica que a sincronização está em curso. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do AutoPilot

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Grupos**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Introduza um **Nome do grupo** e uma **Descrição do grupo**.
    3. Para **Tipo de associação**, selecione **Atribuído** ou **Dispositivo Dinâmico**.
3. Se optou por **Atribuído** para o **Tipo de associação** no passo anterior, no painel **Grupo**, selecione **Membros** e adicione dispositivos do AutoPilot ao grupo.
    Os dispositivos do AutoPilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Se acima optou por **Dispositivo Dinâmico** para o **Tipo de associação**, no painel **Grupo**, selecione **Membros de dispositivo dinâmicos** e escreva o seguinte código na caixa **Regra avançada**.
    - Se quiser criar um grupo que inclua todos os seus dispositivos do AutoPilot, escreva `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Se quiser criar um grupo que inclua todos os seus dispositivos do AutoPilot com um ID do pedido específico, escreva `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Se quiser criar um grupo que inclua todos os seus dispositivos do AutoPilot com um ID de Ordem de Compra específico, escreva `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Depois de adicionar o código da **Regra avançada**, selecione **Guardar**.
5. Selecione **Criar**.



## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do AutoPilot
Os perfis de implementação do AutoPilot são utilizados para configurar os dispositivos AutoPilot.
1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.
2. Escreva um **Nome** e uma **Descrição** opcional.
3. Para **Modo de implementação**, selecione uma destas duas opções:
    - **Orientado pelo utilizador**: os dispositivos com este perfil são associados ao utilizador que inscreve o dispositivo. São necessárias credenciais de utilizador para aprovisionar o dispositivo.
    - **Implementação personalizada (pré-visualização)**: (Versão 17672 ou posterior do Windows 10 Insider Preview) os dispositivos com este perfil não são associados ao utilizador que inscreve o dispositivo. Não são necessárias credenciais de utilizador para aprovisionar o dispositivo.
4. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
5. Selecione **Experiência de configuração inicial (OOBE)**, configure as seguintes opções e, em seguida, selecione**Guardar**:
    - **Idioma (Região)**\*: selecione o idioma a utilizar para o dispositivo. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Configurar automaticamente o teclado**\*: se um **Idioma (Região)** estiver selecionado, ignore a página de seleção do teclado. Esta opção só está disponível se tiver optado pela **Implementação personalizada** no **Modo de implementação**.
    - **Contrato de licença do utilizador final (EULA)**: (Versão 1709 ou posterior do Windows 10) selecione se pretende ou não apresentar o EULA aos utilizadores.
    - **Definições de privacidade**: selecione se pretende ou não apresentar definições de privacidade aos utilizadores.
    - **Tipo de conta de utilizador**: selecione se o tipo de conta do utilizador é **Administrador** ou utilizador **Padrão**. 

6. Selecione **Criar** para criar o perfil. O perfil de implementação do AutoPilot está agora disponível para atribuir a dispositivos.

*As opções **Idioma (Região)** e **Configurar automaticamente o teclado** só estão disponíveis se tiver optado pela **Implementação personalizada (pré-visualização)** no **Modo de implementação** (Versão 17672 ou posterior do Windows 10 Insider Preview).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Atribuir um perfil de implementação do AutoPilot a um grupo de dispositivos

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis de implementação** e selecione um perfil.
2. No painel do perfil específico, selecione **Atribuições**. 
3. Escolha **Selecionar Grupos** e, em seguida, no painel **Selecionar grupos**, escolha os grupos aos quais pretende atribuir o perfil. Em seguida, clique em **Selecionar**.

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do AutoPilot
Após ter criado um perfil de implementação do AutoPilot, poderá editar determinadas partes do perfil de implementação.   

1. No [Intune, no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos**.
2. Em **Inscrição no Windows**, na secção **Windows AutoPilot**, selecione **Perfis de Implementação**.
3. Selecione o perfil que pretende editar.
4. À esquerda, clique em **Propriedades** para alterar o nome ou a descrição do perfil de implementação. Após ter efetuado as alterações, clique em **Guardar**.
5. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> As alterações ao perfil são aplicadas aos dispositivos atribuídos a esse perfil. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 163236 -->
Pode ver um alerta que apresenta o número de dispositivos do programa AutoPilot que não têm perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos.

Para ver alertas de dispositivos não atribuídos, no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Descrição geral** > **Dispositivos não atribuídos**.  

## <a name="delete-autopilot-devices"></a>Eliminar dispositivos Autopilot

Pode eliminar dispositivos do Windows AutoPilot que não estejam inscritos.

1. Se os dispositivos estiverem inscritos no Intune, primeiro tem de [eliminá-los do portal do Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição do Windows** > **Dispositivos**.

3. Em **Dispositivos Windows AutoPilot**, escolha os dispositivos que quer eliminar e, em seguida, **Eliminar**.

4. Confirme a eliminação ao escolher **Sim**. A eliminação pode demorar alguns minutos.

## <a name="using-autopilot-in-other-portals"></a>Utilizar o AutoPilot noutros portais
Se não estiver interessado na gestão de dispositivos móveis, poderá utilizar o AutoPilot na Microsoft Store para Empresas, por exemplo. Embora a utilização de outros portais seja uma opção, recomendamos-lhe que apenas utilize o Intune para gerir as suas implementações do AutoPilot. Se utilizar o Intune e outro portal, o Intune não será capaz de:
- Apresentar alterações aos perfis criados no Intune que tenham sido editados noutro portal
- Sincronizar perfis criados noutro portal
- Apresentar alterações a atribuições de perfil efetuadas noutro portal
- Sincronizar atribuições de perfil efetuadas noutro portal
- Apresentar as alterações à lista de dispositivos que foram feitas noutro portal

## <a name="next-steps"></a>Próximos passos
Após ter configurado o Windows AutoPilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
