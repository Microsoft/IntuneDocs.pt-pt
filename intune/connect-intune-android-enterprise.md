---
title: Ligar a sua conta do Intune à sua conta do Android Enterprise
titlesuffix: Microsoft Intune
description: Saiba como ligar a sua conta do Intune à sua conta do Android Enterprise.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 421d9c56f959fe30d35c0c55ce34017a7a0ba5a6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838265"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Ligar a sua conta do Intune à sua conta do Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para suportar [perfil do Android work](android-work-profile-enroll.md), [Android totalmente gerido](android-fully-managed-enroll.md), e [dispositivos dedicados do Android](android-kiosk-enroll.md), tem de ligar a conta de inquilino do Intune para a sua empresa Android conta.  

> [!NOTE]
> Devido a uma interação entre os domínios da Google e da Microsoft, poderá ser necessário ajustar as definições do browser.  Certifique-se de que tanto "portal.azure.com" como "play.google.com" se encontram na mesma zona de segurança do seu browser.

1. Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md) como **Microsoft Intune**.
2. Inicie sessão no [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido**.  Se estiver a utilizar uma função de administrador do Intune personalizada, o acesso a esta opção requer permissões de Atualização e Leitura da Organização.
   
   ![Ecrã de inscrição do Android Enterprise](./media/android-work-bind.png)

3. Selecione **Concordo** para conceder permissão à Microsoft para [enviar informações sobre o utilizador e o dispositivo à Google](data-intune-sends-to-google.md). 
   
4. Selecione **Inicie o Google para ligar agora** para abrir o site da Google Play Store Gerida. O site abre num novo separador do seu browser.
  
5. Na página de início de sessão da Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android Enterprise deste inquilino. Esta é a conta Google que os administradores de TI da sua empresa partilham para gerir e publicar aplicações na consola Google Play. Pode utilizar uma conta Google existente ou criar uma nova. A conta que escolher não pode estar associada a um domínio do G Suite.
    
    > [!Note]
    > Se estiver a utilizar o browser Microsoft Edge, clique em **Iniciar Sessão** no canto superior direito para iniciar sessão na sua conta Google.

6. Na opção **Nome da organização**, forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor **Microsoft Intune**.

7. Concorde com o contrato Android e, em seguida, selecione **Confirmar**. O seu pedido será processado.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Desligar a sua conta administrativa do Android Enterprise

Pode desativar a gestão e inscrição do Android Enterprise. Para tal, tem de remover todos os dispositivos com perfil de trabalho do Android inscritos. Em seguida, selecione **Desligar** na consola de administração do Intune para remover todos os dispositivos com perfil de trabalho do Android e dispositivos de quiosque Android inscritos. Esta ação também remove a relação entre a conta Android Enterprise e o Intune.

1. Como administrador do Intune, no [portal do Azure](https://portal.azure.com), selecione **Todos os Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Inscrição de dispositivos** > **Inscrição Android** > **Google Play Gerido** > **Desligar**.
3. Selecione **Sim** para desligar e anular a inscrição dos dispositivos Android Enterprise do Intune.

## <a name="next-steps"></a>Passos Seguintes

Depois de ligar à conta do Android Enterprise, pode [configurar dispositivos com perfil de trabalho do Android](android-work-profile-enroll.md) e [configurar dispositivos de quiosque Android](android-kiosk-enroll.md).
