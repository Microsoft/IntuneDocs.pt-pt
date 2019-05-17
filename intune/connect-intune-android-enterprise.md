---
title: Ligar a conta do Intune à conta do Managed Google Play
titleSuffix: Microsoft Intune
description: Saiba como ligar a conta do Intune à conta do Managed Google Play.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19efd0821deeac0e76c60ee67e6230da554391a0
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898018"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Ligue a conta do Intune à conta do Managed Google Play

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para suportar o [Perfil de trabalho do Android Enterprise](android-work-profile-enroll.md), o [Android Enterprise totalmente gerido](android-fully-managed-enroll.md) e os [Dispositivos dedicados do Android Enterprise](android-kiosk-enroll.md), tem de ligar a conta de inquilino do Intune à conta do Managed Google Play.  

> [!NOTE]
> Devido a uma interação entre os domínios da Google e da Microsoft, poderá ser necessário ajustar as definições do browser.  Certifique-se de que tanto "portal.azure.com" como "play.google.com" se encontram na mesma zona de segurança do seu browser.

1. Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sessão no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido**.  Se estiver a utilizar uma função de administrador do Intune personalizada, o acesso a esta opção requer permissões de Atualização e Leitura da Organização.
   
   ![Ecrã de inscrição do Android Enterprise](./media/android-work-bind.png)

3. Selecione **Concordo** para conceder permissão à Microsoft para [enviar informações sobre o utilizador e o dispositivo à Google](data-intune-sends-to-google.md). 
   
4. Selecione **Inicie o Google para ligar agora** para abrir o site da Google Play Store Gerida. O site abre num novo separador do seu browser.
  
5. Na página de início de sessão do Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android Enterprise deste inquilino. Esta é a conta Google que os administradores de TI da sua empresa partilham para gerir e publicar aplicações na consola Google Play. Pode utilizar uma conta Google existente ou criar uma nova. A conta que escolher não pode estar associada a um domínio do G Suite.
    
    > [!Note]
    > Se estiver a utilizar o browser Microsoft Edge, clique em **Iniciar Sessão** no canto superior direito para iniciar sessão na sua conta Google.

6. Na opção **Nome da organização**, forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor **Microsoft Intune**.

7. Concorde com o contrato Android e, em seguida, selecione **Confirmar**. O seu pedido será processado.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desligar a conta administrativa do Android Enterprise

Pode desativar a gestão e a inscrição do Android Enterprise. Para tal, tem de remover todos os dispositivos com perfil de trabalho do Android Enterprise inscritos. Em seguida, escolha **Desligar** na consola de administração do Intune para remover todos os dispositivos com perfil de trabalho do Android Enterprise e dispositivos dedicados inscritos. Esta ação também remove a relação entre a conta do Managed Google Play e o Intune.

1. Como administrador do Intune, no [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido** > **Desligar**.
3. Selecione **Sim** para desligar e anular a inscrição dos dispositivos Android Enterprise do Intune.

## <a name="next-steps"></a>Próximos passos

Depois de ligar à conta do Managed Google Play, pode [configurar dispositivos com perfil de trabalho do Android Enterprise](android-work-profile-enroll.md) e [configurar dispositivos dedicados do Android Enterprise](android-kiosk-enroll.md).
