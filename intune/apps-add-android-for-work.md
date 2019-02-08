---
title: Atribuir aplicações Google Play gerido em dispositivos Android enterprise
titlesuffix: Microsoft Intune
description: Compreenda como sincronizar e atribuir aplicações a dispositivos empresariais Android a partir da loja Google Play gerido.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/25/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b68206fd2170dd2bc156d844ae83caafaa08180
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836579"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Adicionar aplicações da Google Play gerido em dispositivos Android enterprise com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android empresarial é um programa para dispositivos de perfil de trabalho Android, dispositivos dedicados/quiosque e dispositivos totalmente geridos. Para os dispositivos com perfil de trabalho do Android, o Android Enterprise é um conjunto de funcionalidades e serviços que separa as aplicações e dados pessoais de aplicações e dados de trabalho. O Android Enterprise fornece privacidade e opções de gestão adicionais quando as pessoas utilizam os respetivos dispositivos Android para o trabalho. O Intune ajuda-o a implementar aplicações e definições em dispositivos com perfil de trabalho do Android, de modo a garantir a separação de informações pessoais e profissionais. Todas as aplicações que instala em dispositivos com perfil de trabalho do Android são provenientes da Google Play Store Gerida. A forma como atribui aplicações em dispositivos com perfil de trabalho do Android é diferente em dispositivos Android padrão. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las. Em seguida, a aplicação aparece no nó **Aplicações licenciadas** do portal do Azure e pode gerir a atribuição da aplicação como faria com qualquer outra aplicação.

Além disso, se tiver criado as suas próprias aplicações de linha de negócio (LOB), pode atribuí-las do seguinte modo:
- Inscreva-se numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store.
- Sincronize as aplicações com o Intune.

## <a name="before-you-start"></a>Antes de começar

Verifique se configurou o Intune e os perfis de trabalho do Android para trabalharem em conjunto na carga de trabalho **Inscrição de dispositivos** do portal do Azure. Para obter mais informações, veja [Inscrever dispositivos Android](android-work-profile-enroll.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

## <a name="managed-google-play-app-type"></a>Tipo de aplicação do Google Play gerido 
O **managed Google Play** tipo de aplicação permite-lhe adicionar especificamente [aplicações da Google Play gerido](https://play.google.com/work/search?q=microsoft&c=apps) ao Intune. Como o administrador do Intune, pode agora navegar, procurar, aprovar, sincronizar e atribuir aprovados Google Play gerido aplicações no Intune.  Já não precisar de procurar na consola do Google Play gerido separadamente e já não tem de autenticar. 

> [!NOTE]
> Se preferir sincronizar uma aplicação do Google Play gerido com o Intune, consulte o artigo [sincronizar uma aplicação do Google Play gerido com o Intune](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>Adicionar uma aplicação da Google Play gerido com o Intune

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. Na **Intune** painel, selecione **aplicações de cliente** > **aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na **tipo de aplicação** na caixa pendente, selecione **Google Play gerido**.
7. Selecione **Google Play gerido - aprovar aplicações** para serach para aplicações aprovadas da Google Play gerido.
8. Clique em cada aplicação que pretende incluir. Em seguida, c
9. Clique em **aprovar** para aprovar a aplicação do Google Play gerido e clique em **aprovar** para aceitar as permissões de aplicações. 
10. Clique em **OK** para incluir a aplicação (ões).
11. Clique em **Add** sobre o **aplicação aplicações** painel sincronizar com o serviço Google Play gerido.

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>Sincronizar uma aplicação do Google Play gerido com o Intune (alternativa)
Se preferir sincronizar uma aplicação do Google Play gerido com o Intune, em vez de adicioná-lo diretamente com o Intune, utilize os seguintes passos.

> [!IMPORTANT]
> As informações fornecidas abaixo são um método alternativo para adicionar uma aplicação do Google Play gerido com o Intune, conforme descrito acima.

### <a name="synchronize-an-app-from-the-managed-google-play-store"></a>Sincronizar uma aplicação a partir da Google Play Store Gerida

1. Aceda à [Google Play Store Gerida](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
2. Procure na loja e selecione a aplicação que quer atribuir através do Intune.
3. Na página que apresenta a aplicação, selecione **Aprovar**.  
    O seguinte exemplo mostra a aplicação Microsoft Excel escolhida.

    ![O botão Aprovar na Google Play Store Gerida](media/approve.png)
    
   É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. 

4. Selecione **Aprovar** para aceitar as permissões da aplicação e continuar.

    ![O botão Aprovar das permissões de aplicações](media/approve-app-permissions.png)

5. Selecione uma opção para processar novos pedidos de permissão de aplicações e, em seguida, selecione **Guardar**.

    ![Opções para processar novos pedidos de permissões de aplicações](media/approve-app-settings.png)

    A aplicação foi aprovada e é apresentada na consola de administração de TI. Em seguida, pode [sincronizar a aplicação de perfil de trabalho do Android com o Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune). 

### <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizar uma aplicação da Google Play Store Gerida com o Intune

Se tiver aprovado uma aplicação a partir da loja e não a vir no nó **Aplicações licenciadas** da carga de trabalho **Aplicações do cliente**, force uma sincronização imediata da seguinte forma:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel de carga de trabalho **Aplicações do cliente**, em **Configuração**, selecione **Google Play Gerido**.
5. No painel **Google Play Gerido**, selecione **Atualizar**.  
    A página atualizará a hora e o estado da última sincronização.
6. No painel de carga de trabalho **Aplicações do cliente**, selecione **Aplicações**.  
    É apresentada a aplicação Google Play Store Gerida que ficou recentemente disponível.

## <a name="assigning-the-managed-google-play-app"></a>Atribuição da aplicação do Google Play gerido

Quando a aplicação é apresentada no **licenças de aplicações** nó da **aplicações de cliente** painel de carga de trabalho, pode [atribuí-la tal como atribuiria qualquer outra aplicação](/intune-azure/manage-apps/deploy-apps) atribuindo o a aplicação grupos de utilizadores.

Após atribuir a aplicação, esta será instalada nos dispositivos direcionados. Não é pedida aprovação da instalação ao utilizador do dispositivo.

## <a name="manage-android-enterprise-app-permissions"></a>Gerir permissões de aplicações do Android Enterprise
O Android Enterprise necessita que aprove aplicações na consola Web da Google Play Store Gerida antes de as sincronizar com o Intune e de as atribuir aos seus utilizadores. Uma vez que o Android Enterprise lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões das aplicações em nome de todos os seus utilizadores. Os utilizadores não veem as permissões das aplicações durante a instalação das aplicações, pelo que é importante que compreenda as permissões.

Quando o programador de uma aplicação atualiza as permissões com uma nova versão da aplicação, as permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão anterior da aplicação podem continuar a utilizá-la. No entanto, a aplicação não é atualizada até serem aprovadas as novas permissões. Os dispositivos sem a aplicação instalada só desinstalam a aplicação quando aprovar as novas permissões novas da aplicação.

### <a name="update-app-permissions"></a>Atualizar permissões de aplicações

Visite periodicamente a consola do managed Google Play para verificar a existência de novas permissões. Pode configurar o Google Play para enviar para si ou para outras pessoas um e-mail sempre que sejam necessárias novas permissões para uma aplicação aprovada. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões ao seguir os seguintes passos:

1. Aceda ao [Google Play](https://play.google.com/work).
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Selecione o separador **Atualizações** e verifique se alguma aplicação requer uma atualização.  
    Todas as aplicações indicadas necessitam de novas permissões e só são atribuídas depois de aplicadas.

Em alternativa, pode configurar o Google Play para reaprovar automaticamente as permissões por aplicação. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Trabalhar com uma aplicação de linha de negócio a partir da Google Play Store Gerida

1. Inicie sessão na [Google Play Developer Console](https://play.google.com/apps/publish) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.  
    Se estiver a iniciar sessão pela primeira vez, terá de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
2. Na consola, selecione **Adicionar nova aplicação**.
3. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)**.

    ![Apenas disponibilizar a aplicação para a sua organização](media/restrict.png)

    Esta operação disponibiliza a aplicação apenas para a sua organização. Não ficará disponível na Google Play Store pública.

    Para obter mais informações sobre como carregar e publicar aplicações Android, veja a [Ajuda da Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Depois de publicar a sua aplicação, inicie sessão na [Google Play Store Gerida](https://play.google.com/work) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
5. No nó **Aplicações** da loja, verifique se a aplicação que publicou é apresentada.  
    A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="delete-managed-google-play-apps"></a>Eliminar as aplicações da Google Play gerido 
Quando for necessário, pode eliminar as aplicações geridas do Google Play do Microsoft Intune. Para eliminar uma aplicação do Google Play gerida, abra o Microsoft Intune no portal do Azure e selecione **aplicações de cliente** > **aplicações**. Da lista de aplicações, selecione as reticências (...) à direita da aplicação do Google Play gerida, em seguida, selecione **eliminar** na lista apresentada. Quando elimina uma aplicação do Google Play gerida da lista de aplicações, a aplicação do Google Play gerida é automaticamente não aprovada.

## <a name="next-steps"></a>Passos Seguintes

- [Atribuir aplicações a grupos](apps-deploy.md) 

