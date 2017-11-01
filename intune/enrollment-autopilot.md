---
title: Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment
description: Saiba como inscrever novos dispositivos Windows 10 com o Programa Windows AutoPilot Deployment.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 83ab9e4a6fae4fda4c8e97c5fc091d4e5a03f3ea
ms.sourcegitcommit: b8d3f8da6d8c2bd5d6140d538193a02d5875aefb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/27/2017
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>Inscrever dispositivos Windows com o Programa Windows AutoPilot Deployment
O Programa Windows AutoPilot Deployment simplifica o aprovisionamento de dispositivos. Hoje em dia, a criação e manutenção de imagens de sistema operativo personalizadas é algo que demora bastante tempo. Também poderá demorar bastante tempo a aplicar estas imagens de sistema operativo personalizadas a novos dispositivos para prepará-las para utilização antes de as fornecer aos seus utilizadores finais. Com o Microsoft Intune e o AutoPilot, pode fornecer novos dispositivos aos seus utilizadores finais sem ter de criar, manter e aplicar imagens de sistema operativo personalizadas aos dispositivos. Ao utilizar o Intune para gerir dispositivos AutoPilot, pode gerir políticas, perfis, aplicações, entre outros, nos dispositivos após estes serem inscritos. Para uma descrição geral das vantagens, cenários e pré-requisitos, veja [Descrição geral do Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).

## <a name="prerequisites"></a>Pré-requisitos
- [Os dispositivos têm de estar registados na sua organização](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot#registering-devices-to-your-organization)
- [A Inscrição automática no Windows tem de estar ativada](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Subscrição do Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>Sincronizar dispositivos
Sincronize os seus dispositivos registados no Intune para poder configurá-los.

1. Inicie sessão no [Azure](https://portal.azure.com/).
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
4. No painel **Inscrição no Windows**, na secção **Programa Windows AutoPilot Deployment**, selecione **Dispositivos**.
5. Clique em **Sincronizar** para importar os seus dispositivos registados. Uma mensagem indica que a sincronização está em curso.
6. Atualize a vista para ver os novos dispositivos. O processo poderá demorar alguns minutos a concluir, consoante o número de dispositivos em sincronização.  

## <a name="create-an-autopilot-deployment-profile"></a>Criar um perfil de implementação do AutoPilot
Os perfis de implementação do AutoPilot são utilizados para configurar os dispositivos AutoPilot.
1. Inicie sessão no [Azure](https://portal.azure.com/). 
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
4. No painel **Inscrição no Windows**, na secção **Programa Windows AutoPilot Deployment**, selecione **Perfis de Implementação**.
5. Clique em **Criar Perfil** e selecione um nome e uma descrição opcional. 
6. Para **Tipo de associação**, selecione **Associado ao Azure AD**.
7. Para uma **Experiência de configuração inicial (OOBE)**, configure as seguintes opções e, em seguida, clique em **OK**: 
   - **Definições de privacidade**: selecione se pretende apresentar definições de privacidade aos utilizadores. 
   - **Contrato de licença do utilizador final (EULA)**: selecione se pretende apresentar o EULA aos utilizadores.
   - **Tipo de conta de utilizador**: selecione se o tipo de conta de utilizador é um **Administrador** ou utilizador **Padrão**.

     > [!Note]    
     > Esta definição não se aplica a contas de Administrador Global ou de Administrador da Empresa. Estas contas não podem ser de utilizadores padrão porque têm acesso a todas as funcionalidades administrativas no Azure AD.
8. Clique em **Criar** para criar o perfil. O perfil de implementação do AutoPilot está agora disponível para atribuir a dispositivos.
     
> [!Note]    
> As seguintes definições estão configuradas com todos os perfis de implementação do AutoPilot:
> - Ignorar páginas de configuração de registo do OEM, Cortana e OneDrive
> - Configuração automática para trabalho ou escola
> - Experiência de início de sessão com marca escolar ou empresarial    

## <a name="assign-an-autopilot-deployment-profile"></a>Atribuir um perfil de implementação do AutoPilot
Após a criação de perfis de implementação do AutoPilot, poderá atribui-los a dispositivos selecionados.

1. Inicie sessão no [Azure](https://portal.azure.com/). 
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
4. No painel **Inscrição no Windows**, na secção **Programa Windows AutoPilot Deployment**, selecione **Dispositivos**.
5. Selecione os dispositivos aos quais quer atribuir o perfil de implementação. Poderá filtrar na coluna **Estado** para encontrar facilmente dispositivos sem um perfil atribuído. 
6. Clique em **Atribuir perfil**, selecione o perfil de implementação do AutoPilot e, em seguida, clique em **Atribuir**. Uma mensagem indica que a atribuição está em curso.
7. Atualize a vista para verificar que o perfil foi atribuído aos dispositivos. O processo poderá demorar alguns minutos a concluir, dependendo do número de dispositivos selecionados. 

> [!Note]
> O novo perfil é atribuído ao dispositivo. No entanto, o perfil não será aplicado aos dispositivos já inscritos no Intune até que o dispositivo tenha sido reposto e reinscrito.

### <a name="assign-a-different-autopilot-deployment-profile"></a>Atribuir um perfil de implementação do AutoPilot diferente
Após ter atribuído um perfil de implementação do AutoPilot a um dispositivo, se decidir atribuir um perfil diferente, atribua o novo perfil ao dispositivo.  

## <a name="edit-an-autopilot-deployment-profile"></a>Editar um perfil de implementação do AutoPilot 
Após ter criado um perfil de implementação do AutoPilot, poderá editar determinadas partes do perfil de implementação.   
1. Inicie sessão no [Azure](https://portal.azure.com/). 
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, selecione **Inscrição de dispositivos**.
4. No painel **Inscrição no Windows**, na secção **Programa Windows AutoPilot Deployment**, selecione **Perfis de Implementação**. 
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

## <a name="next-steps"></a>Próximos passos
Após ter configurado o Windows AutoPilot para dispositivos Windows 10 registados, saiba como gerir esses dispositivos. Para obter mais detalhes, veja [O que é a gestão de dispositivos do Microsoft Intune?](https://docs.microsoft.com/intune/device-management)