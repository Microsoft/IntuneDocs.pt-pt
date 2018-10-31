---
title: Tutorial – Utilizar o Autopilot para inscrever dispositivos no Intune
titleSuffix: Microsoft Intune
description: Neste tutorial, vai configurar o Windows Autopilot para inscrever dispositivos no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.openlocfilehash: a90f53bfc5841cc0f773751e7df917d8fc8b6cf8
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2018
ms.locfileid: "49431939"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Tutorial: Utilizar o Autopilot para inscrever dispositivos Windows no Intune
O Windows Autopilot simplifica a inscrição de dispositivos. Com o Microsoft Intune e o Autopilot, pode disponibilizar novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas. 

Neste tutorial, ficará a saber como:
> [!div class="checklist"]
> * Adicionar dispositivos ao Intune
> * Criar um grupo de dispositivos do Autopilot
> * Criar um perfil de implementação do Autopilot
> * Atribuir um perfil de implementação do Autopilot ao grupo de dispositivos
> * Distribuir dispositivos Windows pelos utilizadores

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](free-trial-sign-up.md).

Para obter uma descrição geral dos benefícios, cenários e pré-requisitos do Autopilot, veja [Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) (Descrição geral do Windows Autopilot).


## <a name="prerequisites"></a>Pré-requisitos
- [Configurar a inscrição automática no Windows](quickstart-setup-auto-enrollment.md)
- [Subscrição do Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Adicionar dispositivos

O primeiro passo na configuração do Windows Autopilot é adicionar os dispositivos Windows ao Intune. Tudo o que precisa de fazer é criar um ficheiro CSV e importá-lo para o Intune.

1. Em qualquer editor de texto, crie uma lista de valores separados por vírgulas (CSV) que identificam os dispositivos Windows. Utilize o seguinte formato:
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    Os primeiros três itens são obrigatórios, mas o ID da encomenda é opcional.

2. Guarde o ficheiro CSV.

3. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

4. Em **Adicionar dispositivos Windows Autopilot**, procure o ficheiro CSV que guardou.

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

5. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Depois de a importação estar concluída, escolha **Inscrição de dispositivos** > **Inscrição no Windows** > **Windows Autopilot** > **Dispositivos** > **Sincronizar**. Uma mensagem indica que a sincronização está em curso. A conclusão do processo poderá demorar alguns minutos, consoante o número de dispositivos que está a sincronizar.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

Em seguida, vai criar um grupo de dispositivos e colocar os dispositivos Autopilot que acabou de carregar nesse grupo.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Grupos** > **Novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Em **Nome do grupo**, introduza *Grupo do Autopilot*. Em **Descrição do grupo**, introduza *Grupo de teste para dispositivos Autopilot*.
    3. Em **Tipo de associação**, escolha **Atribuído**.
3. No painel **Grupo**, escolha **Membros** e adicione os dispositivos Autopilot ao grupo. Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot

Depois de criar um grupo de dispositivos, tem de criar um perfil de implementação para poder configurar os dispositivos Autopilot.

1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Dispositivos** > **Importar**.
2. Em **Nome**, introduza *Perfil Autopilot*. Em **Descrição**, introduza *Testar o perfil para dispositivos Autopilot*.
3. Defina **Converter todos os dispositivos visados para o Autopilot** como **Sim**. Esta definição garante que todos os dispositivos na lista são registados com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar.
4. Em **Modo de implementação**, escolha **Controlado pelo utilizador**. Os dispositivos com este perfil estão associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
5. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
6. Escolha **Experiência de configuração inicial (OOBE)**, configure as seguintes opções, mantenha as predefinições das opções restantes e, em seguida, selecione**Guardar**:
    - **Contrato de licença do utilizador final (EULA)**:**Ocultar**
    - **Definições de privacidade**: **Mostrar**
    - **Tipo de conta de utilizador**: **Padrão**

6. Selecione **Criar** para criar o perfil. O perfil de implementação do Autopilot está agora disponível para atribuir a dispositivos.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Atribuir um perfil de implementação do Autopilot a um grupo de dispositivos

Agora que o perfil de implementação foi criado, vai atribuí-lo ao grupo de dispositivos.
1. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição no Windows** > **Perfis de implementação** e selecione um perfil.
2. No painel do perfil específico, selecione **Atribuições**. 
3. Escolha **Selecionar grupos**, em seguida, no painel **Selecionar grupos**, escolha **Grupo do Autopilot** e escolha **Selecionar**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Agora pode distribuir os dispositivos Windows pelos seus utilizadores. Quando iniciarem sessão pela primeira vez, o sistema do Autopilot irá automaticamente inscrever e configurar os dispositivos. 

## <a name="clean-up-resources"></a>Limpar recursos

Se já não quiser utilizar os dispositivos Autopilot, poderá eliminá-los.

1. Se os dispositivos estiverem inscritos no Intune, primeiro tem de [eliminá-los do portal do Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. No [Intune no portal do Azure](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição do Windows** > **Dispositivos**.

3. Em **Dispositivos Windows Autopilot**, escolha os dispositivos que quer eliminar e, em seguida, **Eliminar**.

4. Confirme a eliminação ao escolher **Sim**. A eliminação pode demorar alguns minutos.

## <a name="next-steps"></a>Próximos passos

Pode encontrar mais informações sobre outras opções disponíveis para o Windows Autopilot.

> [!div class="nextstepaction"]
> [Artigo de inscrição do Autopilot detalhado](enrollment-autopilot.md)

