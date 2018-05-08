---
title: Atribuir aplicações a dispositivos Android for Work
titlesuffix: Microsoft Intune
description: Compreenda como sincronizar e atribuir aplicações em dispositivos Android for Work a partir da Google Play for Work Store.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1742c33642667a9e7b8ca2f780094345959cd86c
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
---
# <a name="assign-apps-to-android-for-work-devices-with-intune"></a>Atribuir aplicações em dispositivos Android for Work com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Android for Work é um programa para dispositivos Android. Todas as aplicações que instala em dispositivos Android for Work são provenientes da Google Play for Work Store. As aplicações em dispositivos Android for Work são atribuídas de forma diferente da atribuição em dispositivos Android padrão. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las. Em seguida, a aplicação aparece no nó **Aplicações licenciadas** do portal do Azure e pode gerir a atribuição da aplicação como faria com qualquer outra aplicação.

Além disso, se tiver criado as suas próprias aplicações de linha de negócio (LOB), pode atribuí-las do seguinte modo:
- Inscreva-se numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store.
- Sincronize as aplicações com o Intune.

## <a name="before-you-start"></a>Antes de começar

Verifique se configurou o Intune e o Android for Work para trabalharem em conjunto na carga de trabalho **Inscrição de dispositivos** do portal do Azure.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizar uma aplicação a partir da Google Play for Work Store

1. Aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
2. Procure na loja e selecione a aplicação que quer atribuir através do Intune.
3. Na página que apresenta a aplicação, selecione **Aprovar**.  
    O seguinte exemplo mostra a aplicação Microsoft Excel escolhida.

    ![O botão Aprovar na Google Play for Work Store](media/approve.png)
    
   É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. 

4. Selecione **Aprovar** para aceitar as permissões da aplicação e continuar.

    ![O botão Aprovar das permissões de aplicações](media/approve-app-permissions.png)

5. Selecione uma opção para processar novos pedidos de permissão de aplicações e, em seguida, selecione **Guardar**.

    ![Opções para processar novos pedidos de permissões de aplicações](media/approve-app-settings.png)

    A aplicação foi aprovada e é apresentada na consola de administração de TI. Em seguida, pode [sincronizar a aplicação Android for Work com o Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizar uma aplicação Android for Work com o Intune

Se tiver aprovado uma aplicação a partir da loja e não a vir no nó **Aplicações licenciadas** da carga de trabalho **Aplicações móveis**, force uma sincronização imediata da seguinte forma:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. No painel de carga de trabalho **Aplicações móveis**, em **Configuração**, selecione **Android for Work**.
5. No painel **Android for Work**, selecione **Sincronizar**.  
    A página atualizará a hora e o estado da última sincronização.
6. No painel de carga de trabalho **Aplicações móveis**, selecione **Aplicações**.  
    É apresentada a aplicação Android for Work recentemente disponibilizada.

Quando a aplicação for apresentada no nó **Licenças de aplicações** do painel de carga de trabalho **Aplicações móveis**, pode [atribuí-la tal como atribuiria qualquer outra aplicação](/intune-azure/manage-apps/deploy-apps). Só pode atribuir a aplicação em grupos de utilizadores.

Após atribuir a aplicação, esta será instalada nos dispositivos direcionados. Não é pedida aprovação da instalação ao utilizador do dispositivo.

## <a name="manage-android-for-work-app-permissions"></a>Gerir permissões de aplicações Android for Work
O Android for Work precisa que aprove aplicações na consola Web do managed Google Play antes de as sincronizar com o Intune e de as atribuir aos seus utilizadores. Uma vez que o Android for Work lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões das aplicações em nome de todos os seus utilizadores. Os utilizadores não veem as permissões das aplicações durante a instalação das aplicações, pelo que é importante que leia e compreenda as permissões.

Quando o programador de uma aplicação publica uma nova versão da aplicação com permissões atualizadas, as permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão anterior da aplicação podem continuar a utilizá-la. No entanto, a aplicação não é atualizada até serem aprovadas as novas permissões. Os dispositivos sem a aplicação instalada só desinstalam a aplicação quando aprovar as novas permissões novas da aplicação.

### <a name="update-app-permissions"></a>Atualizar permissões de aplicações

Visite periodicamente a consola do managed Google Play para verificar a existência de novas permissões. Pode configurar o Google Play para enviar para si ou para outras pessoas um e-mail sempre que sejam necessárias novas permissões para uma aplicação aprovada. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões ao fazer o seguinte:

1. Aceda ao [Google Play](http://play.google.com/work).
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Selecione o separador **Atualizações** e verifique se alguma aplicação requer uma atualização.  
    Todas as aplicações indicadas necessitam de novas permissões e só são atribuídas depois de aplicadas.

Em alternativa, pode configurar o Google Play para reaprovar automaticamente as permissões por aplicação. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Trabalhar com uma aplicação de linha de negócio a partir da Google Play for Work Store

1. Inicie sessão na [Google Play Developer Console](https://play.google.com/apps/publish) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.  
    Se estiver a iniciar sessão pela primeira vez, terá de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
2. Na consola, selecione **Adicionar nova aplicação**.
3. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)**.

    ![Apenas disponibilizar a aplicação para a sua organização](media/restrict.png)

    Esta operação garante que a aplicação apenas está disponível para a sua organização e não está disponível na Google Play Store pública.

    Para obter mais informações sobre como carregar e publicar aplicações Android, veja a [Ajuda da Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Depois de publicar a aplicação, inicie sessão na [Google Play for Work Store](https://play.google.com/work) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
5. No nó **Aplicações** da loja, verifique se a aplicação que publicou é apresentada.  
    A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md) 

