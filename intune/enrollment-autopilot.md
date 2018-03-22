---
title: Inscrever dispositivos com o Programa Windows AutoPilot Deployment
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Windows 10 com o Programa Windows AutoPilot Deployment.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 4522be0b636a72844fa6177fbb35d3350cfbd00e
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2018
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot-deployment-program"></a>Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment
O Programa Windows AutoPilot Deployment simplifica o aprovisionamento de dispositivos. A criação e manutenção de imagens personalizadas do sistema operativo são um processo moroso. Também poderá demorar a aplicar estas imagens personalizadas do sistema operativo a novos dispositivos para as preparar para utilização antes de as disponibilizar aos seus utilizadores finais. Com o Microsoft Intune e o AutoPilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos AutoPilot, pode gerir políticas, perfis, aplicações, entre outros, nos dispositivos após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

## <a name="prerequisites"></a>Pré-requisitos
- [Os dispositivos têm de estar registados na sua organização](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot#device-registration-and-oobe-customization)
- [A Inscrição automática no Windows tem de estar ativada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Subscrição do Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Sincronizar dispositivos
Sincronize os seus dispositivos registados no Intune para poder configurá-los.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Em **Intune**, escolha **Inscrição de dispositivos**.
4. Selecione **Inscrição no Windows** e na secção **Programa de Implementação do Windows AutoPilot**, selecione **Dispositivos**.
5. Clique em **Sincronizar** para importar os seus dispositivos registados. Uma mensagem indica que a sincronização está em curso.
6. Atualize a vista para ver os novos dispositivos. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do AutoPilot
Os perfis de implementação do AutoPilot são utilizados para configurar os dispositivos AutoPilot.
1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Em **Intune**, escolha **Inscrição de dispositivos**.
4. Selecione **Inscrição no Windows** e na secção **Programa de Implementação do Windows AutoPilot**, selecione **Perfis de Implementação**.
5. Selecione **Criar Perfil** e selecione um nome e descrição opcionais.
6. Para **Aderir ao Azure AD como**, selecione **Associado ao Azure AD**.
7. Para uma **Experiência de configuração inicial (OOBE)**, configure as seguintes opções e, em seguida, clique em **Guardar**:

   - **Contrato de licença do utilizador final (EULA)**: selecione se pretende apresentar o EULA aos utilizadores.
   - **Definições de privacidade**: selecione se pretende apresentar definições de privacidade aos utilizadores.
   - **Tipo de conta de utilizador**: selecione se o tipo de conta de utilizador é um **Administrador** ou utilizador **Padrão**.

     > [!Note]    
     > Esta definição não se aplica a contas de Administrador Global ou de Administrador da Empresa. Estas contas não podem ser de utilizadores padrão porque têm acesso a todas as funcionalidades administrativas no Azure AD.


6. Clique em **Criar** para criar o perfil. O perfil de implementação do AutoPilot está agora disponível para atribuir a dispositivos.

> [!Note]    
> As seguintes definições estão configuradas com todos os perfis de implementação do AutoPilot:
> - Ignorar páginas de configuração de registo do OEM, Cortana e OneDrive
> - Configuração automática para trabalho ou escola
> - Experiência de início de sessão com marca escolar ou empresarial    

## <a name="assign-an-autopilot-deployment-profile"></a>Atribuir um perfil de implementação do AutoPilot
Após a criação de perfis de implementação do AutoPilot, poderá atribui-los a dispositivos selecionados.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Em **Intune**, escolha **Inscrição de dispositivos**.
4. Selecione **Inscrição no Windows** e na secção **Programa de Implementação do Windows AutoPilot**, selecione **Dispositivos**.
5. Selecione os dispositivos aos quais quer atribuir o perfil de implementação. Poderá filtrar na coluna **Estado do Perfil** para encontrar facilmente dispositivos sem um perfil atribuído.
6. Clique em **Atribuir perfil**, selecione o perfil de implementação do AutoPilot e, em seguida, clique em **Atribuir**. Uma mensagem indica que a atribuição está em curso.
7. Atualize a vista para verificar que o perfil foi atribuído aos dispositivos. O processo poderá demorar alguns minutos a concluir, dependendo do número de dispositivos selecionados.

> [!Note]
> O novo perfil é atribuído ao dispositivo. Para dispositivos já inscritos no Intune, o perfil é aplicado depois de o dispositivo ser reposto e reinscrito.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Atribuir um perfil de implementação do AutoPilot diferente
Após ter atribuído um perfil de implementação do AutoPilot a um dispositivo, se decidir atribuir um perfil diferente, atribua o novo perfil ao dispositivo.  

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do AutoPilot
Após ter criado um perfil de implementação do AutoPilot, poderá editar determinadas partes do perfil de implementação.   

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Em **Intune**, escolha **Inscrição de dispositivos**.
4. Em **Inscrição no Windows**, na secção **Programa Windows AutoPilot Deployment**, escolha **Perfis de Implementação**.
5. Selecione o perfil que pretende editar.
6. À esquerda, clique em **Propriedades** para alterar o nome ou a descrição do perfil de implementação. Após ter efetuado as alterações, clique em **Guardar**.
7. Clique em **Definições** para efetuar alterações às definições da OOBE. Após ter efetuado as alterações, clique em **Guardar**.

> [!NOTE]
> O perfil atualizado é atribuído aos dispositivos. No entanto, o perfil atualizado não será aplicado a um dispositivo já inscrito no Intune até que o dispositivo tenha sido reposto e reinscrito.

## <a name="using-autopilot-in-other-portals"></a>Utilizar o AutoPilot noutros portais
Se não estiver interessado na gestão de dispositivos móveis, poderá utilizar o AutoPilot na Loja Microsoft para Empresas, por exemplo. Embora a utilização de outros portais seja uma opção, recomendamos-lhe que apenas utilize o Intune para gerir as suas implementações do AutoPilot. Se utilizar o Intune e outro portal, o Intune não será capaz de:
- Apresentar alterações aos perfis criados no Intune que tenham sido editados noutro portal
- Sincronizar perfis criados noutro portal
- Apresentar alterações a atribuições de perfil efetuadas noutro portal
- Sincronizar atribuições de perfil efetuadas noutro portal
- Apresentar as alterações à lista de dispositivos que foram feitas noutro portal

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertas para dispositivos Windows AutoPilot não atribuídos  <!-- 163236 -->
Pode ver um alerta para dispositivos Windows AutoPilot não atribuídos para ver o número de dispositivos do programa AutoPilot que não tem perfis de implementação do AutoPilot atribuídos. Utilize as informações no alerta para criar perfis e atribui-los aos dispositivos não atribuídos. Quando clica no alerta, é-lhe apresentada uma lista completa dos dispositivos Windows AutoPilot e informações detalhadas sobre os mesmos.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. Em **Intune**, escolha **Inscrição de dispositivos**.
4. Para ver o alerta, escolha **Descrição geral**. Clique no alerta para ver uma lista de dispositivos AutoPilot.  


## <a name="next-steps"></a>Próximos passos
Após ter configurado o Windows AutoPilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais informações, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)
