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
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b0bb0bd1f0df3aeb4185542d424bd3ffffe42cd
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036547"
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

Se não tiver uma subscrição do Intune, [inscreva-se numa conta de avaliação gratuita](../fundamentals/free-trial-sign-up.md).

Para obter uma descrição geral dos benefícios, cenários e pré-requisitos do Autopilot, veja [Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot) (Descrição geral do Windows Autopilot).


## <a name="prerequisites"></a>Pré-requisitos
- [Configurar a inscrição automática no Windows](../quickstart-setup-auto-enrollment.md)
- [Assinatura Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Adicionar dispositivos

O primeiro passo na configuração do Windows Autopilot é adicionar os dispositivos Windows ao Intune. Tudo o que precisa de fazer é criar um ficheiro CSV e importá-lo para o Intune.

1. Em qualquer editor de texto, crie uma lista de valores separados por vírgulas (CSV) que identificam os dispositivos Windows. Utilize o seguinte formato:
    
    *número de série*, *Windows-Product-ID*, *hardware-hash*, *opcional-Group-tag*
    
    Os três primeiros itens são necessários, mas a marca Group (anteriormente conhecida como "ID do pedido") é opcional.

2. Guarde o ficheiro CSV.

3. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **dispositivos** **Windows** > (no programa de **implantação do Windows AutoPilot** > **importar**.

    ![Captura de ecrã dos dispositivos Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

4. Em **Adicionar dispositivos Windows Autopilot**, procure o ficheiro CSV que guardou.

    ![Captura de ecrã de Adicionar dispositivos Windows Autopilot](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. Escolha **Importar** para iniciar a importação das informações do dispositivo. A importação poderá demorar alguns minutos.

4. Após a conclusão da importação, escolha **dispositivos** > **Windows** > **registro do Windows** > **dispositivos** (no programa de **implantação do Windows AutoPilot** > **sincronizar**. Uma mensagem exibe que a sincronização está em andamento. A conclusão do processo poderá demorar alguns minutos, consoante o número de dispositivos que está a sincronizar.

5. Atualize a vista para ver os novos dispositivos.

## <a name="create-an-autopilot-device-group"></a>Criar um grupo de dispositivos do Autopilot

Em seguida, vai criar um grupo de dispositivos e colocar os dispositivos Autopilot que acabou de carregar nesse grupo.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **grupos** > **novo grupo**.
2. No painel **Grupo**:
    1. Para **Tipo de grupo**, selecione **Segurança**.
    2. Em **Nome do grupo**, introduza *Grupo do Autopilot*. Em **Descrição do grupo**, introduza *Grupo de teste para dispositivos Autopilot*.
    3. Em **Tipo de associação**, escolha **Atribuído**.
3. No painel **Grupo**, escolha **Membros** e adicione os dispositivos Autopilot ao grupo. Os dispositivos Autopilot que ainda não estão inscritos são dispositivos em que o nome é igual ao número de série do dispositivo.
4. Selecione **Criar**.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do Autopilot

Depois de criar um grupo de dispositivos, tem de criar um perfil de implementação para poder configurar os dispositivos Autopilot.

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > perfis de **implantação** > **Criar perfil**.
2. Na página **noções básicas** , **nome**do Tor, insira o *perfil do AutoPilot*. Em **Descrição**, introduza *Testar o perfil para dispositivos Autopilot*.
3. Defina **Converter todos os dispositivos visados para o Autopilot** como **Sim**. Esta definição garante que todos os dispositivos na lista são registados com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar.
4. Selecione **Seguinte**.
5. Na página de **OOBE (experiência do usuário)** , para o modo de **implantação**, escolha **orientado por usuários**. Os dispositivos com este perfil estão associados ao utilizador que inscreve o dispositivo. Precisa de credenciais de utilizador para inscrever o dispositivo.
6. Na caixa **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
7. Configure as seguintes opções e deixe outras definidas como o padrão:
    - **Contrato de licença do utilizador final (EULA)** :**Ocultar**
    - **Definições de privacidade**: **Mostrar**
    - **Tipo de conta de utilizador**: **Padrão**
8. Selecione **Seguinte**.
9. Na página **atribuições** , escolha **grupos selecionados** para **atribuir a**.
10. Escolha **Selecionar grupos a serem incluídos**, escolha **grupo piloto automático**.
11. Selecione **Seguinte**.
12. Na página **revisar + criar** , escolha **criar** para criar o perfil.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Agora pode distribuir os dispositivos Windows pelos seus utilizadores. Quando iniciarem sessão pela primeira vez, o sistema do Autopilot irá automaticamente inscrever e configurar os dispositivos. 

## <a name="clean-up-resources"></a>Limpar recursos

Se você não quiser mais usar os dispositivos de piloto automático, poderá excluí-los.

1. Se os dispositivos estiverem inscritos no Intune, primeiro tem de [eliminá-los do portal do Azure Active Directory](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **windows** > **registro do Windows** > **dispositivos** (em programa de **implantação do Windows AutoPilot**).

3. Escolha os dispositivos que você deseja excluir e, em seguida, escolha **excluir**.

4. Confirme a eliminação ao escolher **Sim**. A eliminação pode demorar alguns minutos.

## <a name="next-steps"></a>Próximos passos

Pode encontrar mais informações sobre outras opções disponíveis para o Windows Autopilot.

> [!div class="nextstepaction"]
> [Artigo de inscrição do Autopilot detalhado](enrollment-autopilot.md)


