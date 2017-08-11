---
title: Inscrever dispositivos Android no Intune
titleSuffix: Intune on Azure
description: Saiba como inscrever dispositivos Android no Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 183e60af4d6174c18fc3883f2cdd9827505d2aba
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/09/2017
---
# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enquanto administrador do Intune, este permite-lhe gerir dispositivos Android, incluindo dispositivos Samsung Knox Standard. Também pode gerir o perfil de trabalho nos [dispositivos Android for Work](#enable-enrollment-of-android-for-work-devices).

Os dispositivos com o Samsung KNOX Standard são suportados para gestão de vários utilizadores pelo Intune. Deste modo, os utilizadores finais podem iniciar e terminar sessão no dispositivo com as credenciais do Azure AD e o dispositivo será gerido centralmente quer esteja a ser utilizado ou não. Quando os utilizadores finais iniciam sessão, têm acesso às aplicações e obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

## <a name="prerequisite"></a>Pré-requisito

Tem de definir a autoridade de MDM **Microsoft Intune** para se preparar para gerir dispositivos móveis. Veja [Set the MDM authority (Definir a autoridade de MDM)](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.

## <a name="set-up-android-enrollment"></a>Configurar inscrição do Android

Por predefinição, o Intune permite a inscrição de dispositivos Android e Samsung Knox Standard.

Para impedir a inscrição de dispositivos Android ou apenas de dispositivos Android pessoais, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md).

Para ativar a gestão de dispositivos, os seus utilizadores têm de inscrever os dispositivos deles ao transferir a aplicação Portal da Empresa do Intune disponível no Google Play e, em seguida, ao abrir a aplicação e seguir as instruções de inscrição. Assim que os dispositivos Android estiverem geridos, pode [atribuir políticas de conformidade](compliance-policy-create-android.md), [gerir aplicações](app-management.md) e mais.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Ativar a inscrição de dispositivos Android for Work

Para ativar a gestão de perfis de trabalho em dispositivos que [suportam Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), tem de adicionar um enlace do Android for Work para Intune. Para inscrever dispositivos que suportam o Android for Work mas que foram anteriormente inscritos como dispositivos Android normais, a inscrição dos dispositivos tem de ser anulada e, em seguida efetuada novamente.

## <a name="add-android-for-work-binding-for-intune"></a>Adicionar o Enlace do Android for Work para Intune

1. **Configurar o Intune MDM**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md) como **Microsoft Intune**.
2. **Configurar o enlace do Android for Work**<br>
    Como administrador do Intune, no Portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

    1. No painel **Intune**, escolha **Inscrição de dispositivos**, > **Inscrição de Android for Work** e clique em **Configurar** para abrir o site do Android for Work do Google Play. Esta ação irá abrir um novo separador no seu browser.
  ![Captura de ecrã que mostra uma ligação ao enlace Configurar o Android for Work](./media/android-work-bind.png)

    2. **Iniciar sessão no Google**<br>
   Na página de início de sessão da Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android for Work deste inquilino. Esta é a conta Google partilhada pelos administradores de TI da sua organização que geriam e publicavam aplicações na consola do Play for Work.

    3. **Fornecer detalhes da organização**<br>
   Na opção **Nome da organização** forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor *Microsoft Intune*. Concorde com o contrato Android for Work e, em seguida, clique em **Confirmar**. O seu pedido será processado.

## <a name="specify-android-for-work-enrollment-settings"></a>Especificar as Definições de Inscrição do Android for Work
   O Android for Work só é suportado em determinados dispositivos Android. Veja os [requisitos Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") da Google. Qualquer dispositivo que suporte o Android for Work também irá suportar a gestão Android convencional.  O Intune permite-lhe especificar como os dispositivos que suportam o Android for Work são geridos:

   - **Gerir todos os dispositivos como Android** – todos os dispositivos Android, incluindo os dispositivos que suportam o Android for Work, serão inscritos como dispositivos Android convencionais.
   - **Gerir dispositivos suportados como Android for Work** – todos os dispositivos que suportam o Android for Work são inscritos como dispositivos Android for Work. Qualquer dispositivo Android que não suporte o Android for Work é inscrito como um dispositivo Android convencional.
   - **Gerir dispositivos suportados para utilizadores apenas nestes grupos de utilizadores como Android for Work** – permite-lhe direcionar a gestão do Android for Work a um conjunto limitado de utilizadores. Apenas os membros destes grupos selecionados que inscrevam um dispositivo que suporte o Android for Work são inscritos como dispositivos Android for Work. Todos os outros dispositivos são inscritos como dispositivos Android. Esta funcionalidade é útil durante os testes piloto do Android for Work.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicar aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Terá de indicar aos utilizadores finais para acederem ao Google Play para transferir a aplicação Portal da Empresa do Intune e, em seguida, para abrirem a aplicação e seguirem as instruções para inscrever os seus dispositivos. A aplicação guia os utilizadores ao longo do processo de inscrição ao explicar aquilo que os utilizadores podem esperar e que os administradores de TI poderão ver ou não nos seus dispositivos.

Também poderá enviar-lhes uma ligação para os passos de inscrição online: [Inscrever o seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Para obter informações sobre outras tarefas do utilizador final, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Anular o enlace da conta administrativa do Android for Work

Pode desativar a gestão e inscrição do Android for Work. Ao clicar em **Unbind** na consola de administração do Intune, remove todos os dispositivos Android for Work inscritos e remove a relação entre a conta Android for Work e o Intune.

### <a name="how-to-unbind-an-android-for-work-account"></a>Como anular o enlace de uma conta Android for Work

1. **Anular o enlace do Android for Work**<br>
    Como administrador do Intune, no Portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.  No painel **Intune**, escolha **Inscrição de dispositivos**, > **Inscrição do Android for Work** e, em seguida, **Anular o enlace**.

2. **Concorde com a eliminação do enlace do Android for Work**<br>
  Clique em **Sim** para eliminar o enlace e anular a inscrição de todos os dispositivos Android for Work do Intune.
