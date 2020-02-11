---
title: Ligar a conta do Intune à conta do Managed Google Play
titleSuffix: Microsoft Intune
description: Saiba como ligar a conta do Intune à conta do Managed Google Play.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 581d88e49391bc874625e9c84318c039706b0c1b
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124831"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Ligue a conta do Intune à conta do Managed Google Play

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para suportar o [Perfil de trabalho do Android Enterprise](android-work-profile-enroll.md), o [Android Enterprise totalmente gerido](android-fully-managed-enroll.md) e os [Dispositivos dedicados do Android Enterprise](android-kiosk-enroll.md), tem de ligar a conta de inquilino do Intune à conta do Managed Google Play.  

Para facilitar a configuração e utilização da gestão do Android Enterprise, ao ligar-se ao Google Play, a Intune irá adicionar automaticamente quatro aplicações comuns relacionadas com o Android Enterprise à consola de administração Intune. As quatro aplicações Android Enterprise são as seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usado para Android Enterprise cenários totalmente geridos.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Ajuda-o a iniciar sessão nas suas contas se utilizar a verificação de dois fatores.
- **[Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usado para políticas de proteção de aplicações (APP) e cenários de perfil de trabalho Android Enterprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usado para cenários dedicados/quiosques Android Enterprise.

> [!NOTE]
> Devido a uma interação entre os domínios da Google e da Microsoft, poderá ser necessário ajustar as definições do browser.  Certifique-se de que tanto "portal.azure.com" como "play.google.com" se encontram na mesma zona de segurança do seu browser.

1. Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](../fundamentals/mdm-authority-set.md) como **Microsoft Intune**.
2. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431), escolha **dispositivos** > **Android** > **Android > ** **Managed Google Play**.  Se estiver a utilizar uma função de administrador do Intune personalizada, o acesso a esta opção requer permissões de Atualização e Leitura da Organização.
   
   ![Ecrã de inscrição do Android Enterprise](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Selecione **Concordo** para conceder permissão à Microsoft para [enviar informações sobre o utilizador e o dispositivo à Google](../protect/data-intune-sends-to-google.md). 
   
4. Selecione **Inicie o Google para ligar agora** para abrir o site da Google Play Store Gerida. O site abre num novo separador do seu browser.
  
5. Na página de início de sessão do Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android Enterprise deste inquilino. Esta é a conta Google que os administradores de TI da sua empresa partilham para gerir e publicar aplicações na consola Google Play. Pode utilizar uma conta Google existente ou criar uma nova. A conta que escolher não pode estar associada a um domínio do G Suite.
    
    > [!Note]
    > Se estiver a utilizar o browser Microsoft Edge, clique em **Iniciar Sessão** no canto superior direito para iniciar sessão na sua conta Google.

6. Na opção **Nome da organização**, forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor **Microsoft Intune**.

7. Concorde com o contrato Android e, em seguida, selecione **Confirmar**. O seu pedido será processado.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desligar a conta administrativa do Android Enterprise

Pode desativar a gestão e a inscrição do Android Enterprise. Para isso, primeiro deve retirar quaisquer dispositivos Android Enterprise matriculados, incluindo dispositivos de perfil de trabalho, dispositivos dedicados e dispositivos totalmente geridos. Em seguida, escolha **desligar** na consola de administração Intune para remover todos os dispositivos de perfil de trabalho Android Enterprise inscritos, dispositivos dedicados e dispositivos totalmente geridos a partir da inscrição. Esta ação também remove a relação entre a conta do Managed Google Play e o Intune.

1. Como administrador intune, inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Escolha **dispositivos** ** > ** android > **android inscrição** > **Managed Google Play** > **Disconnect**.
3. Selecione **Sim** para desligar e anular a inscrição dos dispositivos Android Enterprise do Intune.

## <a name="next-steps"></a>Passos Seguintes

Depois de se ligar à conta Gerida do Google Play, pode [configurar dispositivos](android-work-profile-enroll.md)de perfil de trabalho Android Enterprise, [configurar dispositivos dedicados](android-kiosk-enroll.md) ao Android Enterprise e [configurar dispositivos geridos pelo Android Enterprise](android-fully-managed-enroll.md)
