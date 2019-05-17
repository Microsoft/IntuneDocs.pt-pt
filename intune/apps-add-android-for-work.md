---
title: Atribuir aplicações do Managed Google Play a dispositivos Android Enterprise
titleSuffix: Microsoft Intune
description: Saiba como sincronizar e atribuir aplicações a dispositivos Android Enterprise a partir da loja do Managed Google Play.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b977d60c982a43e4465cd451cc2fc24b4e69f4cf
ms.sourcegitcommit: 1cae690ca2ac6cc97bbcdf656f54b31878297ae8
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59898112"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Adicionar aplicações do Managed Google Play a dispositivos Android Enterprise com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O Android Enterprise é um programa para dispositivos com perfil de trabalho do Android, dispositivos dedicados/de quiosque e dispositivos totalmente geridos. Para os dispositivos com perfil de trabalho do Android, o Android Enterprise é um conjunto de funcionalidades e serviços que separa as aplicações e os dados pessoais de aplicações e dados de trabalho. O Android Enterprise fornece privacidade e opções de gestão adicionais quando as pessoas utilizam os seus dispositivos Android para o trabalho. O Intune ajuda-o a implementar aplicações e definições em dispositivos com perfil de trabalho do Android, de modo a garantir a separação de informações pessoais e profissionais. Todas as aplicações que instala em dispositivos com perfil de trabalho do Android são provenientes da Google Play Store Gerida. A forma como atribui aplicações em dispositivos com perfil de trabalho do Android é diferente em dispositivos Android padrão. Deve iniciar sessão na loja, procurar as aplicações desejadas e aprová-las. Em seguida, a aplicação aparece no nó **Aplicações licenciadas** do portal do Azure e pode gerir a atribuição da aplicação como faria com qualquer outra aplicação.

Além disso, se tiver criado as suas próprias aplicações de linha de negócio (LOB), pode atribuí-las do seguinte modo:
- Inscreva-se numa conta Google Developer que lhe permita publicar aplicações numa área privada na Google Play Store.
- Sincronize as aplicações com o Intune.

## <a name="before-you-start"></a>Antes de começar

Verifique se configurou o Intune e os perfis de trabalho do Android para trabalharem em conjunto na carga de trabalho **Inscrição de dispositivos** do portal do Azure. Para obter mais informações, veja [Inscrever dispositivos Android](android-work-profile-enroll.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

## <a name="managed-google-play-app-type"></a>Tipo de aplicações do Managed Google Play
O tipo de aplicações do **Managed Google Play** permite-lhe adicionar especificamente [aplicações do Managed Google Play](https://play.google.com/work/search?q=microsoft&c=apps) ao Intune. Como administrador do Intune, pode agora procurar, pesquisar, aprovar, sincronizar e atribuir aplicações do Managed Google Play aprovadas no Intune.  Já não precisa de procurar na consola do Managed Google Play separadamente e já não tem de se autenticar novamente.

> [!NOTE]
> Se preferir sincronizar uma aplicação do Managed Google Play com o Intune, veja [Sincronizar uma aplicação do Managed Google Play com o Intune](apps-add-android-for-work.md#synchronize-a-managed-google-play-app-with-intune-alternative)

## <a name="add-a-managed-google-play-app-using-intune"></a>Adicionar uma aplicação do Managed Google Play através do Intune

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**.  
    O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Aplicações cliente** > **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na caixa pendente **Tipo de aplicação**, selecione **Managed Google Play**.
7. Selecione **Managed Google Play – Aprovar** para abrir o catálogo do Managed Google Play.
8. Utilize a caixa de pesquisa para procurar as aplicações que pretende incluir.
9. Clique em **Aprovar** para aprovar a aplicação no Managed Google Play e clique em **Aprovar** para aceitar as permissões da aplicação.
10. Selecione **Manter aprovado quando as aplicações pedirem novas permissões** na janela Definições de Aprovação e, em seguida, clique em **Guardar**. Se não escolher esta opção, terá de aprovar manualmente quaisquer novas permissões, caso o programador da aplicação publique uma atualização. Tal fará com que as instalações e atualizações da aplicação parem até que as permissões sejam aprovadas. Por este motivo, é recomendado selecionar a opção para aprovar automaticamente as novas permissões. 
11. Clique em **OK** para incluir a aplicação (ou aplicações) que aprovou.
12. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play.

## <a name="synchronize-a-managed-google-play-app-with-intune-alternative"></a>Sincronizar uma aplicação do Managed Google Play com o Intune (Alternativa)
Se preferir sincronizar uma aplicação do Managed Google Play com o Intune, em vez de a adicionar diretamente através do Intune, utilize os seguintes passos.

> [!IMPORTANT]
> As informações fornecidas abaixo são um método alternativo para adicionar uma aplicação do Managed Google Play através do Intune, conforme descrito acima.

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

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos de perfil de trabalho do Android Enterprise

Quando a aplicação for apresentada no nó **Licenças de aplicações** do painel de carga de trabalho **Aplicações cliente**, pode [atribuí-la tal como faria com qualquer outra aplicação](/intune-azure/manage-apps/deploy-apps) ao atribuir a aplicação aos grupos de utilizadores.

Após atribuir a aplicação, esta será instalada nos dispositivos direcionados. Não é pedida aprovação da instalação ao utilizador do dispositivo. Para obter mais informações sobre os dispositivos de perfil de trabalho do Android Enterprise, veja [Configurar a inscrição de dispositivos de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md).

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos totalmente geridos do Android Enterprise

Os [dispositivos totalmente geridos do Android Enterprise](android-fully-managed-enroll.md) são dispositivos pertencentes à empresa associados a um único utilizador e utilizados exclusivamente para o trabalho e não para uso pessoal. Os utilizadores em dispositivos totalmente geridos podem obter as aplicações da empresa disponíveis na aplicação do Managed Google Play no dispositivo.

Por predefinição, um dispositivo totalmente gerido do Android Enterprise não permitirá que os funcionários instalem quaisquer aplicações que não sejam aprovadas pela organização. Além disso, os funcionários não poderão remover quaisquer aplicações instaladas que poderia ir contra a política. Se quiser permitir que os utilizadores acedam à Google Play Store completa para instalarem aplicações, em vez de terem acesso apenas a aplicações aprovadas na loja do Managed Google Play, poderá definir **Permitir o acesso a todas as aplicações na Google Play Store** como **Permitir**. Com esta definição, o utilizador pode aceder a todas as aplicações na Google Play Store com a conta empresarial, mas as compras podem ser limitadas. Pode remover a restrição de compras limitadas ao permitir que os utilizadores adicionem novas contas ao dispositivo. Se o fizer, permitirá que os utilizadores finais possam comprar aplicações na Google Play Store com as contas pessoais, bem como efetuar compras na aplicação. Para obter mais informações, veja [Definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades com o Intune](device-restrictions-android-for-work.md). 

> [!NOTE]
> A aplicação do Microsoft Intune e a aplicação do Microsoft Authenticator serão instaladas como aplicações necessárias em todos os dispositivos totalmente geridos durante a integração. Ter essas aplicações instaladas automaticamente fornece suporte de acesso condicional e os utilizadores da aplicação do Microsoft Intune podem ver e resolver problemas de conformidade. 

## <a name="manage-android-enterprise-app-permissions"></a>Gerir permissões de aplicações do Android Enterprise
O Android Enterprise necessita que aprove as aplicações na consola Web do Managed Google Play para as poder sincronizar com o Intune e as atribuir aos utilizadores. Uma vez que o Android Enterprise lhe permite transferir automática e silenciosamente estas aplicações para os dispositivos dos utilizadores, tem de aceitar as permissões das aplicações em nome de todos os utilizadores. Os utilizadores não veem as permissões das aplicações durante a instalação das aplicações, pelo que é importante que compreenda as permissões.

Quando o programador de uma aplicação atualiza as permissões com uma nova versão da aplicação, as permissões não são automaticamente aceites, mesmo que tenha aprovado as permissões anteriores. Os dispositivos que executam a versão anterior da aplicação podem continuar a utilizá-la. No entanto, a aplicação não é atualizada até serem aprovadas as novas permissões. Os dispositivos sem a aplicação instalada só desinstalam a aplicação quando aprovar as novas permissões novas da aplicação. 

### <a name="update-app-permissions"></a>Atualizar permissões de aplicações

Visite periodicamente a consola do managed Google Play para verificar a existência de novas permissões. Pode configurar o Google Play para enviar para si ou para outras pessoas um e-mail sempre que sejam necessárias novas permissões para uma aplicação aprovada. Se atribuir uma aplicação e observar que esta não está instalada nos dispositivos, verifique se existem novas permissões ao seguir os seguintes passos:

1. Aceda ao [Google Play](https://play.google.com/work).
2. Inicie sessão com a conta Google que utilizou para publicar e aprovar as aplicações.
3. Selecione o separador **Atualizações** e verifique se alguma aplicação requer uma atualização.  
    Todas as aplicações indicadas necessitam de novas permissões e só são atribuídas depois de aplicadas.

Em alternativa, pode configurar o Google Play para reaprovar automaticamente as permissões por aplicação.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Relatórios adicionais da aplicação do Managed Google Play para dispositivos de perfil de trabalho do Android Enterprise

Para as aplicações do Managed Google Play implementadas para dispositivos de perfil de trabalho do Android Enterprise, pode ver o número de versão específica da aplicação instalada num dispositivo. Tal só se aplica às aplicações obrigatórias. 

## <a name="working-with-a-line-of-business-app-from-the-managed-google-play-store"></a>Trabalhar com uma aplicação de linha de negócio a partir da Google Play Store Gerida

1. Inicie sessão na [Consola do Programador do Google Play](https://play.google.com/apps/publish) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.  
    Se estiver a iniciar sessão pela primeira vez, terá de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
2. Na consola, selecione **Adicionar nova aplicação**.
3. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)**.

    ![Apenas disponibilizar a aplicação para a sua organização](media/restrict.png)

    Esta operação disponibiliza a aplicação apenas para a sua organização. Não ficará disponível na Google Play Store pública.

    Para obter mais informações sobre como carregar e publicar aplicações Android, veja a [Ajuda da Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Depois de publicar a aplicação, inicie sessão na [loja do Managed Google Play](https://play.google.com/work) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
5. No nó **Aplicações** da loja, verifique se a aplicação que publicou é apresentada.  
    A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="delete-managed-google-play-apps"></a>Eliminar aplicações do Managed Google Play
Quando necessário, pode eliminar as aplicações do Managed Google Play do Microsoft Intune. Para eliminar uma aplicação do Managed Google Play, abra o Microsoft Intune no portal do Azure e selecione **Aplicações cliente** > **Aplicações**. Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
