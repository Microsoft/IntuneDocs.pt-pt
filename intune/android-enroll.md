---
title: Inscrever dispositivos Android no Intune | Documentos da Microsoft
titlesuffix: Azure portal
description: Saiba como inscrever dispositivos Android no Intune.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 12/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ad018bdfa55b030f5d714017ae09f616ae2bf164
ms.sourcegitcommit: 9fabf1a8db53842f7b00762374de5b137158ee25
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/22/2017
---
# <a name="enroll-android-devices"></a>Inscrever dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enquanto administrador do Intune, pode gerir dispositivos Android, incluindo dispositivos Samsung Knox Standard. Também pode gerir o perfil de trabalho nos [dispositivos Android for Work](#enable-enrollment-of-android-for-work-devices).

Os dispositivos com o Samsung Knox Standard são suportados para gestão de vários utilizadores pelo Intune. Isto significa que os utilizadores podem iniciar e terminar sessão num dispositivo com as respetivas credenciais do Azure AD. O dispositivo é gerido centralmente independentemente de estar a ser utilizado. Quando os utilizadores iniciam sessão, têm acesso às aplicações e, além disso, obtêm as políticas aplicadas às mesmas. Quando os utilizadores terminam sessão, todos os dados das aplicações são limpos.

## <a name="prerequisite"></a>Pré-requisito

Para se preparar para gerir dispositivos móveis, tem de definir a autoridade de gestão de dispositivos móveis (MDM) para o **Microsoft Intune**. Veja [Set the MDM authority (Definir a autoridade de MDM)](mdm-authority-set.md) para obter instruções. Este item só é definido uma vez, quando está a configurar pela primeira vez o Intune para a gestão de dispositivos móveis.

## <a name="set-up-android-enrollment"></a>Configurar inscrição do Android

Por predefinição, o Intune permite a inscrição de dispositivos Android e Samsung Knox Standard.

Para impedir a inscrição de dispositivos Android ou apenas de dispositivos Android pessoais, veja [Set device type restrictions (Definir restrições de tipos de dispositivos)](enrollment-restrictions-set.md).

Para ativar a gestão de dispositivos, os seus utilizadores têm de inscrever os respetivos dispositivos ao transferir a aplicação Portal da Empresa do Intune (disponível no Google Play) e, em seguida, ao abrir a aplicação e seguir as instruções. Assim que os dispositivos Android estiverem geridos, pode [atribuir políticas de conformidade](compliance-policy-create-android.md), [gerir aplicações](app-management.md) e mais.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Ativar a inscrição de dispositivos Android for Work

Para ativar a gestão de perfis de trabalho em dispositivos que [suportam Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), tem de adicionar um enlace do Android for Work para Intune. Para inscrever dispositivos que suportam o Android for Work, mas que foram anteriormente inscritos como dispositivos Android normais, tem de cancelar a inscrição dos dispositivos e inscrevê-los novamente.

Se estiver a inscrever dispositivos Android dor Work através de uma conta de [Gestor de Inscrições de Dispositivos](device-enrollment-manager-enroll.md), existe um limite de 10 dispositivos que pode inscrever por conta.

## <a name="add-android-for-work-binding-for-intune"></a>Adicionar o enlace do Android for Work para o Intune

1. **Configurar o Intune MDM**<br>
Se ainda não o fez, prepare a gestão de dispositivos móveis ao [definir a autoridade de gestão de dispositivos móveis](mdm-authority-set.md) como **Microsoft Intune**.
2. **Configurar o enlace do Android for Work**<br>
    Como administrador do Intune, no Portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

   a. No painel **Intune**, selecione **Inscrição de dispositivos** > **Inscrição de Android for Work** e selecione **Configurar** para abrir o site do Android for Work do Google Play. O site abre num novo separador do seu browser.
   ![Captura de ecrã que mostra uma ligação para configurar o enlace do Android for Work](./media/android-work-bind.png)

   b. **Iniciar sessão no Google**<br>
   Na página de início de sessão da Google, introduza a conta Google que será associada a todas as tarefas de gestão do Android for Work deste inquilino. Esta é a conta Google que os administradores de TI da sua empresa partilham para gerir e publicar aplicações na consola Play for Work.

   c. **Fornecer detalhes da organização**<br>
   Na opção **Nome da organização**, forneça o nome da sua empresa. A opção **Fornecedor de Gestão de mobilidade de empresas (EMM)** deverá apresentar o valor **Microsoft Intune**. Concorde com o contrato Android for Work e, em seguida, selecione **Confirmar**. O seu pedido será processado.

## <a name="specify-android-for-work-enrollment-settings"></a>Especificar as definições de inscrição do Android for Work
   O Android for Work só é suportado em determinados dispositivos Android. Veja os [requisitos Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") da Google. Qualquer dispositivo que suporte o Android for Work também suporta a gestão Android convencional. O Intune permite-lhe especificar como os dispositivos que suportam o Android for Work são geridos:

   - **Gerir todos os dispositivos como Android**. Todos os dispositivos Android, incluindo os dispositivos que suportam o Android for Work, serão inscritos como dispositivos Android convencionais.
   - **Gerir dispositivos suportados como Android for Work**. Todos os dispositivos que suportam o Android for Work são inscritos como dispositivos Android for Work. Qualquer dispositivo Android que não suporte o Android for Work é inscrito como um dispositivo Android convencional.
   - **Gerir dispositivos suportados para utilizadores apenas nestes grupos de utilizadores como Android for Work**. Pode direcionar a gestão do Android for Work para um conjunto limitado de utilizadores. Apenas os membros destes grupos selecionados que inscrevam um dispositivo que suporte o Android for Work são inscritos como dispositivos Android for Work. Todos os outros dispositivos são inscritos como dispositivos Android. Esta funcionalidade é útil durante os testes piloto do Android for Work.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Aprovar a aplicação Portal da Empresa na Google Play Store gerida
Tem de aprovar a aplicação Portal da Empresa para Android na Google Play Store gerida para se certificar de que esta recebe atualizações automáticas da aplicação. Se não a aprovar, a aplicação Portal da Empresa irá eventualmente ficar desatualizada e poderá não receber correções importantes ou novas funcionalidades quando forem lançadas pela Microsoft.

Siga estes passos para aprovar o Portal da Empresa do Intune:

1.  Transfira a aplicação Portal da Empresa na [Google Play Store gerida](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Inicie sessão na Google Play Store gerida com a mesma conta Google que utilizou para configurar o enlace do Android for Work.
3.  Clique em **Aprovar**.  Esta ação abrirá uma nova caixa de diálogo.
4.  Reveja as permissões nesta caixa de diálogo e, em seguida, clique em **Aprovar**. Terá de dar estas permissões para permitir que a aplicação Portal da Empresa faça a gestão do perfil de trabalho no dispositivo.
5.  Selecione **Manter aprovado quando as aplicações pedirem novas permissões** e, em seguida, clique em **Guardar**.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicar aos utilizadores como devem inscrever os dispositivos para acederem aos recursos da empresa

Diga aos seus utilizadores para acederem ao Google Play para transferirem a aplicação Portal da Empresa do Intune e, em seguida, para abrirem a aplicação e seguirem as instruções para inscrever os respetivos dispositivos. A aplicação guia os utilizadores ao longo do processo de inscrição ao explicar aquilo que os utilizadores podem esperar e que os administradores de TI poderão ver ou não nos seus dispositivos.

Também poderá enviar-lhes uma ligação para os passos de inscrição online: [Inscrever o seu dispositivo Android no Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Para obter informações sobre outras tarefas do utilizador, veja estes artigos:

- [Recursos sobre a experiência do utilizador final com o Microsoft Intune](end-user-educate.md)
- [Utilizar o dispositivo Android com o Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Anular o enlace da conta administrativa do Android for Work

Pode desativar a gestão e inscrição do Android for Work. Selecionar **Anular o enlace** na consola de administração do Intune remove todos os dispositivos Android for Work inscritos. Esta ação também remove a relação entre a conta Android for Work e o Intune.

### <a name="to-unbind-an-android-for-work-account"></a>Para anular o enlace de uma conta Android for Work

1. **Anular o enlace do Android for Work**<br>
    Como administrador do Intune, no Portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.  No painel **Intune**, selecione **Inscrição de dispositivos**, > **Inscrição do Android for Work** e, em seguida, selecione **Anular o enlace**.

2. **Concorde com a eliminação do enlace do Android for Work**<br>
  Selecione **Sim** para eliminar o enlace e anular a inscrição de todos os dispositivos Android for Work do Intune.
