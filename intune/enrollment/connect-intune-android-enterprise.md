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
ms.openlocfilehash: 0fad076b33bed5375dd8e53dd401a2c9c4c39237
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505568"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Ligue a conta do Intune à conta do Managed Google Play

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para suportar o [Perfil de trabalho do Android Enterprise](android-work-profile-enroll.md), o [Android Enterprise totalmente gerido](android-fully-managed-enroll.md) e os [Dispositivos dedicados do Android Enterprise](android-kiosk-enroll.md), tem de ligar a conta de inquilino do Intune à conta do Managed Google Play.  

Para facilitar a configuração e o uso do gerenciamento corporativo do Android, ao se conectar ao Google Play, o Intune adicionará automaticamente quatro aplicativos comuns do Android Enterprise ao console de administração do Intune. Os quatro aplicativos do Android Enterprise são os seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** -usados para cenários totalmente gerenciados do Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -ajuda você a entrar em suas contas se usar a verificação de dois fatores.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** -usado para as políticas de proteção de aplicativo (aplicativo) e cenários de perfil de trabalho do Android Enterprise.
- [Tela inicial gerenciada](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -usada para cenários do Android Enterprise dedicado/quiosque.

> [!NOTE]
> Devido a uma interação entre os domínios da Google e da Microsoft, poderá ser necessário ajustar as definições do browser.  Certifique-se de que tanto "portal.azure.com" como "play.google.com" se encontram na mesma zona de segurança do seu browser.

1. Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](../fundamentals/mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sessão no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido**.  Se estiver a utilizar uma função de administrador do Intune personalizada, o acesso a esta opção requer permissões de Atualização e Leitura da Organização.
   
   ![Ecrã de inscrição do Android Enterprise](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Selecione **Concordo** para conceder permissão à Microsoft para [enviar informações sobre o utilizador e o dispositivo à Google](../protect/data-intune-sends-to-google.md). 
   
4. Selecione **Inicie o Google para ligar agora** para abrir o site da Google Play Store Gerida. O site abre num novo separador do seu browser.
  
5. Na página de início de sessão do Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android Enterprise deste inquilino. Esta é a conta Google que os administradores de TI da sua empresa partilham para gerir e publicar aplicações na consola Google Play. Pode utilizar uma conta Google existente ou criar uma nova. A conta que escolher não pode estar associada a um domínio do G Suite.
    
    > [!Note]
    > Se estiver a utilizar o browser Microsoft Edge, clique em **Iniciar Sessão** no canto superior direito para iniciar sessão na sua conta Google.

6. Na opção **Nome da organização**, forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor **Microsoft Intune**.

7. Concorde com o contrato Android e, em seguida, selecione **Confirmar**. O seu pedido será processado.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desligar a conta administrativa do Android Enterprise

Pode desativar a gestão e a inscrição do Android Enterprise. Para fazer isso, primeiro você deve desativar qualquer dispositivo Android Enterprise registrado, incluindo dispositivos de perfil de trabalho, dispositivos dedicados e dispositivos totalmente gerenciados. Em seguida, escolha **Desconectar** no console de administração do Intune para remover todos os dispositivos de perfil de trabalho do Android Enterprise registrados, dispositivos dedicados e dispositivos totalmente gerenciados do registro. Esta ação também remove a relação entre a conta do Managed Google Play e o Intune.

1. Como administrador do Intune, entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido** > **Desligar**.
3. Selecione **Sim** para desligar e anular a inscrição dos dispositivos Android Enterprise do Intune.

## <a name="next-steps"></a>Próximos passos

Depois de se conectar à conta de Google Play gerenciado, você pode [configurar dispositivos Android Enterprise Work Profile](android-work-profile-enroll.md), [configurar dispositivos Android Enterprise dedicados](android-kiosk-enroll.md) e [configurar dispositivos Android Enterprise totalmente gerenciados](android-kiosk-enroll.md)
