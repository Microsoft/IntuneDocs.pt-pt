---
title: "Implementar aplicações em dispositivos Android for Work"
description: "Utilize este tópico para sincronizar e, em seguida, implementar aplicações em dispositivos Android for Work a partir da Google Play for Work Store."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 22b842f2745073f0476162278c8b209a3e251f9f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/10/2017
---
# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Como implementar aplicações em dispositivos Android for Work com o Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As aplicações em dispositivos Android for Work são implementadas de forma diferente da implementação em dispositivos Android padrão. Todas as aplicações que instala para o Android for Work provêm da Google Play for Work Store. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las.
Em seguida, a aplicação aparece no nó **Aplicações Compradas em Volume** da consola do Intune. A partir daqui, pode gerir a implementação da aplicação da mesma forma que implementaria qualquer outra aplicação.

Além disso, se tiver criado a as suas próprias aplicações de linha de negócio (LOB), pode implementá-las do seguinte modo:
- Inscreva-se numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store.
- Sincronize as aplicações com o Intune.

## <a name="before-you-start"></a>Antes de começar

Certifique-se de que configurou o Intune e o Android for Work para trabalharem em conjunto no separador **Administrador** da consola do Intune.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Sincronizar uma aplicação a partir da Google Play for Work Store


1. Aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
2. Procure na loja a aplicação que pretende implementar através do Intune.
3. Na página da aplicação que escolheu, selecione **Aprovar**. Neste exemplo, escolheu a aplicação Microsoft Excel.<br>
  ![Exemplo de aprovação de aplicação](media/approve.png)
4. É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações. Selecione **Aprovar** para continuar.<br>
  ![Exemplo de permissões de aprovação de aplicações](media/approve-app-permissions.png)
5. A aplicação foi aprovada e é apresentada na consola de administração de TI.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicar e sincronizar uma aplicação de linha de negócio a partir da Google Play for Work Store

1. Aceda ao Google Play Developer Console, [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work. Se estiver a iniciar sessão pela primeira vez, tem de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
3. Na consola, selecione **Adicionar nova aplicação**.
4. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)**:<br>
  ![Opção para apenas disponibilizar a aplicação para a sua organização](media/restrict.png)<br>
Esta operação garante que a aplicação só está disponível para a sua organização e não está disponível na Google Play Store pública.
Para mais informações sobre como carregar e publicar aplicações Android, consulte a [Ajuda do Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
5. Assim que publicar a sua aplicação, aceda à [Google Play for Work Store](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android for Work.
6. No nó **Aplicações** da loja, verifique se consegue ver a aplicação que publicou. Esta é automaticamente aprovada para sincronizar com o Intune.

## <a name="deploy-an-android-for-work-app"></a>Implementar uma aplicação do Android for Work

Se aprovou uma aplicação a partir da loja e não a vir no nó **Aplicações Compradas em Volume** da área de trabalho **Aplicações**, force uma sincronização imediata da seguinte forma:

1. Na [Consola de administração do Intune](https://manage.microsoft.com), selecione **Admin** > **Mobile Device Management** > **Android for Work**.
2. Na página **Configuração de Gestão de Dispositivos Móveis Android for Work**, selecione **Sincronizar Agora**.
3. A página também apresenta a hora e o estado da última sincronização.

Quando a aplicação é apresentada no nó **Aplicações Compradas em Volume** da área de trabalho **Aplicações**, pode [implementá-la tal como faria com outra aplicação](deploy-apps-in-microsoft-intune.md). Só pode implementar a aplicação em grupos de utilizadores. Atualmente, só pode selecionar as ações **Necessário** e **Desinstalar**.

A capacidade de implementar uma aplicação como **Disponível** aplica a nova experiência de agrupamento e filtragem. As contas do serviço do Intune recentemente aprovisionadas podem utilizar esta funcionalidade quando for lançada. Os clientes existentes do Intune podem utilizar esta funcionalidade quando o inquilino deles tiver sido migrado para o portal do Intune Azure. Os clientes existentes podem criar uma conta de avaliação do Intune para planear e testar esta funcionalidade, até que o inquilino tenha sido migrado.

Após implementar a aplicação, esta será instalada nos dispositivos direcionados. Não é pedida aprovação ao utilizador do dispositivo.

## <a name="manage-app-permissions"></a>Gerir permissões de aplicações
O Android for Work precisa que aprove aplicações na consola Web do managed Google Play antes de as sincronizar com o Intune e de as implementar nos seus utilizadores.  Uma vez que o Android for Work lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões da aplicação em nome de todos os seus utilizadores.  Os utilizadores finais não veem quaisquer permissões de aplicações durante a instalação, pelo que é importante que leia e compreenda estas permissões.

Quando o programador de uma aplicação publica uma nova versão da aplicação com permissões atualizadas, essas permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão antiga da aplicação podem continuar a utilizá-la, mas a aplicação só é atualizada quando as novas permissões forem aprovadas. Os dispositivos sem a aplicação instalada só podem instalar a aplicação quando aprovar as novas permissões novas da aplicação.

### <a name="how-to-update-app-permissions"></a>Como atualizar permissões de aplicações

Visite periodicamente a consola do managed Google Play para verificar a existência de novas permissões. Pode configurar o Google Play para enviar para si ou para outras pessoas um e-mail sempre que sejam necessárias novas permissões para uma aplicação aprovada. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões com seguintes passos:

1. Visite http://play.google.com/work
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Aceda ao separador **Atualizações** para ver se alguma aplicação necessita de uma atualização.  Todas as aplicações indicadas necessitam de novas permissões e só são atribuídas depois de aplicadas.  

Em alternativa, pode configurar o Google Play para reaprovar automaticamente as permissões de aplicações por aplicação. 
