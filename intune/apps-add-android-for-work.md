---
title: "Atribuir aplicações em dispositivos Android for Work | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: utilize este tópico para sincronizar e, em seguida, atribuir aplicações em dispositivos Android for Work a partir da Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 49e86ab665d9022739c0330092734ba897ea3b02
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-assign-apps-to-android-for-work-devices-with-intune"></a>Como atribuir aplicações em dispositivos Android for Work com o Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

As aplicações em dispositivos Android for Work são atribuídas de forma diferente da atribuição em dispositivos Android padrão. Todas as aplicações que instala para o Android for Work provêm da Google Play for Work Store. Deve iniciar sessão na loja, procurar as aplicações pretendidas e aprová-las.
Em seguida, a aplicação aparece no nó **Aplicações licenciadas** do portal do Intune. A partir daqui, pode gerir a atribuição da aplicação da mesma forma que atribuiria qualquer outra aplicação.

Além disso, se tiver criado as suas próprias aplicações de linha de negócio (LOB), pode atribuí-las. Para o fazer, tem de se inscrever numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store e, em seguida, sincronizá-las com o Intune.

## <a name="before-you-start"></a>Antes de começar

Verifique se configurou o Intune e o Android for Work para trabalharem em conjunto na carga de trabalho **Inscrição de dispositivos** do portal do Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizar uma aplicação a partir da Google Play for Work Store


1. Aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
2. Procure na loja a aplicação que pretende atribuir através do Intune.
3. Na página da aplicação que escolheu, selecione **Aprovar**. Neste exemplo, escolheu a aplicação Microsoft Excel.<br>
  ![Exemplo de aprovação de aplicação](media/approve.png)
4. É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. Tem de selecionar **Aprovar** para continuar.<br>
  ![Exemplo de permissões de aprovação de aplicações](media/approve-app-permissions.png)
5. Após alguns momentos, verá uma mensagem a confirmar que a aplicação foi aprovada e está disponível na consola de administração de TI.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicar e sincronizar uma aplicação de linha de negócio a partir da Google Play for Work Store

1. Aceda ao Google Play Developer Console, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work. Se estiver a iniciar sessão pela primeira vez, tem de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
3. Na consola, selecione **Adicionar nova aplicação**.
4. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)** conforme apresentado abaixo.<br>
  ![Opção para apenas disponibilizar a aplicação para a sua organização](media/restrict.png)<br>
Esta ação garante que a aplicação só está disponível para a sua organização e não está disponível na Google Play Store pública.
Para mais informações sobre como carregar e publicar aplicações Android, consulte a [Ajuda do Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Assim que publicar a sua aplicação, aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
6. No nó **Aplicações** da loja, verifique se consegue ver a aplicação que publicou. Tenha em atenção que foi aprovada automaticamente para ser sincronizada com o Intune.

## <a name="assign-an-android-for-work-app"></a>Atribuir uma aplicação do Android for Work

Se tiver aprovado uma aplicação a partir da loja e ainda não a vir no nó **Aplicações licenciadas** da carga de trabalho **Aplicações móveis**, poderá forçar uma sincronização imediata da seguinte forma:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Aplicações móveis**.
4. Na carga de trabalho **Aplicações móveis**, escolha **Configuração** > **Android for Work**.
5. No painel Android for Work, escolha **Sincronizar agora**.
6. A página também apresenta a hora e o estado da última sincronização.

Quando a aplicação é apresentada no nó **Aplicações licenciadas** da carga de trabalho **Aplicações móveis**, pode [atribuí-la tal como atribuiria outra aplicação](/intune-azure/manage-apps/deploy-apps). Só pode atribuir a aplicação em grupos de utilizadores.

Após atribuir a aplicação, esta será instalada nos dispositivos direcionados. Não será pedida aprovação da instalação ao utilizador do dispositivo.

## <a name="manage-app-permissions"></a>Gerir permissões de aplicações
O Android for Work precisa que aprove aplicações na consola Web do managed Google Play antes de as sincronizar com o Intune e de as atribuir nos seus utilizadores.  Uma vez que o Android for Work lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões da aplicação em nome de todos os seus utilizadores.  Os utilizadores finais não irão ver quaisquer permissões de aplicações durante a instalação, pelo que é importante que leia e compreenda estas permissões.

Quando o programador de uma aplicação publica uma nova versão da aplicação com permissões atualizadas, essas permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão antiga da aplicação podem continuar a utilizá-la, mas a aplicação só será atualizada quando as novas permissões forem aprovadas. Os dispositivos sem a aplicação instalada só podem instalar a aplicação quando aprovar as novas permissões novas da aplicação.

### <a name="how-to-update-app-permissions"></a>Como atualizar permissões de aplicações

Periodicamente, deve visitar a consola do managed Google Play para verificar a existência de novas permissões. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões com seguintes passos:

1. Visite http://play.google.com/work
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Aceda ao separador **Atualizações** para ver se alguma aplicação necessita de uma atualização.  Todas as aplicações indicadas necessitam de novas permissões e só serão atribuídas depois de aplicadas.  

