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
ms.openlocfilehash: 4168f78bff8937ca403cdb75b1028954cbbebd6f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Como atribuir aplicações em dispositivos Android for Work com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Android for Work é um programa para dispositivos Android. Todas as aplicações que instala em dispositivos Android for Work são provenientes da Google Play for Work Store. As aplicações em dispositivos Android for Work são atribuídas de forma diferente da atribuição em dispositivos Android padrão. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las. Em seguida, a aplicação aparece no nó **Aplicações licenciadas** do portal do Azure. A partir daqui, pode gerir a atribuição da aplicação da mesma forma que atribuiria qualquer outra aplicação.

Além disso, se tiver criado as suas próprias aplicações de linha de negócio (LOB), pode atribuí-las do seguinte modo:
- Inscreva-se numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store.
- Sincronize as aplicações com o Intune.

## <a name="before-you-start"></a>Antes de começar

Verifique se configurou o Intune e o Android for Work para trabalharem em conjunto na carga de trabalho **Inscrição de dispositivos** do portal do Azure.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizar uma aplicação a partir da Google Play for Work Store

1. Aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
2. Procure na loja e selecione a aplicação que pretende atribuir através do Intune.
3. Selecione **Aprovar** na página que mostra a aplicação. Os seguintes exemplos mostram a aplicação Microsoft Excel que foi escolhida.</br>

    ![Exemplo: aprovar a aplicação na loja do Google Play for Work](media/approve.png)</br>
    
   É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. 

4. Selecione **Aprovar** para aceitar as permissões da aplicação e continuar.</br>

    ![Exemplo: aprovar permissões da aplicação](media/approve-app-permissions.png)

5. Escolha como processar novos pedidos de permissão da aplicação. Em seguida, selecione **Guardar** para guardar a forma como os novos pedidos de permissão da aplicação serão processados.</br>

    ![Exemplo: guardar novos pedidos de permissão da aplicação](media/approve-app-settings.png)</br>

    A aplicação foi aprovada e é apresentada na consola de administração de TI. Agora, pode [sincronizar a aplicação Android for Work com o Intune](apps-add-android-for-work.md#sync-an-android-for-work-app-with-intune). 

## <a name="sync-an-android-for-work-app-with-intune"></a>Sincronizar uma aplicação Android for Work com o Intune

Se tiver aprovado uma aplicação a partir da loja e não a vir no nó **Aplicações licenciadas** da carga de trabalho **Aplicações móveis**, force uma sincronização imediata da seguinte forma:

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, selecione **Android for Work** na secção **Configuração**.
5. No painel Android for Work, selecione **Sincronizar**. A página irá atualizar a hora e o estado da última sincronização.
6. Na carga de trabalho **Aplicações móveis**, selecione **Aplicações** para apresentar a recentemente disponível aplicação Android for Work.

Quando a aplicação for apresentada no nó **Licenças da aplicação** da carga de trabalho **Aplicações móveis**, pode [atribuí-la tal como atribuiria outra aplicação](/intune-azure/manage-apps/deploy-apps). Só pode atribuir a aplicação em grupos de utilizadores.

Após atribuir a aplicação, esta será instalada nos dispositivos direcionados. Não é pedida aprovação da instalação ao utilizador do dispositivo.

## <a name="manage-android-for-work-app-permissions"></a>Gerir permissões de aplicações Android for Work
O Android for Work precisa que aprove aplicações na consola Web do managed Google Play antes de as sincronizar com o Intune e de as atribuir nos seus utilizadores.  Uma vez que o Android for Work lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões da aplicação em nome de todos os seus utilizadores.  Os utilizadores finais não veem quaisquer permissões de aplicações durante a instalação, pelo que é importante que leia e compreenda estas permissões.

Quando o programador de uma aplicação publica uma nova versão da aplicação com permissões atualizadas, essas permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão antiga da aplicação ainda podem utilizá-la. No entanto, a aplicação não é atualizada até serem aprovadas as novas permissões. Os dispositivos sem a aplicação instalada só desinstalam a aplicação quando aprovar as novas permissões novas da aplicação.

### <a name="how-to-update-app-permissions"></a>Como atualizar permissões de aplicações

Visite periodicamente a consola do managed Google Play para verificar a existência de novas permissões. Pode configurar o Google Play para enviar para si ou para outras pessoas um e-mail sempre que sejam necessárias novas permissões para uma aplicação aprovada. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões com seguintes passos:

1. Visite http://play.google.com/work
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Aceda ao separador **Atualizações** para ver se alguma aplicação necessita de uma atualização.  Todas as aplicações indicadas necessitam de novas permissões e só são atribuídas depois de aplicadas.  

Em alternativa, pode configurar o Google Play para reaprovar automaticamente as permissões de aplicações por aplicação. 

## <a name="working-with-a-line-of-business-app-from-the-google-play-for-work-store"></a>Trabalhar com uma aplicação de linha de negócio a partir da Google Play for Work Store

1. Aceda ao Google Play Developer Console, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work. Se estiver a iniciar sessão pela primeira vez, tem de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
3. Na consola, selecione **Adicionar nova aplicação**.
4. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)**:</br>

    ![Opção para apenas disponibilizar a aplicação para a sua organização](media/restrict.png)</br>

Esta operação garante que a aplicação só está disponível para a sua organização e não está disponível na Google Play Store pública.
Para mais informações sobre como carregar e publicar aplicações Android, consulte a [Ajuda do Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Assim que publicar a sua aplicação, aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
6. No nó **Aplicações** da loja, verifique se consegue ver a aplicação que publicou. A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="next-steps"></a>Próximos passos

- [Como atribuir aplicações a grupos](apps-deploy.md)

