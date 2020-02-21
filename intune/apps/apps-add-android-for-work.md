---
title: Atribuir aplicações do Managed Google Play a dispositivos Android Enterprise
titleSuffix: Microsoft Intune
description: Saiba como sincronizar e atribuir aplicações a dispositivos Android Enterprise a partir da loja do Managed Google Play.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: aaed7ec6ba1daa28949b2c1f0997b76135b7e88f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513610"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Adicionar aplicações do Managed Google Play a dispositivos Android Enterprise com o Intune

O Google Play gerido é a loja de aplicações da Google e única fonte de aplicações para android enterprise. Você pode usar Intune para orquestrar implementação de aplicações através do Managed Google Play para qualquer cenário Android Enterprise (incluindo perfil de trabalho, dedicado e inscrições totalmente geridas). A forma como adiciona aplicações geridas do Google Play ao Intune difere da forma como as aplicações Android são adicionadas para a Empresa não Android. As aplicações de loja, apps de linha de negócios (LOB) e aplicações web são aprovadas ou adicionadas ao Managed Google Play, e depois sincronizadas em Intune para que apareçam na lista de Aplicações de Clientes. Assim que aparecerem na lista de Aplicações de Clientes, pode gerir a atribuição de qualquer aplicação Gerida do Google Play como faria com qualquer outra aplicação.

Para facilitar a configuração e utilização da gestão do Android Enterprise, ao ligar o seu inquilino Intune ao Managed Google Play, o Intune irá adicionar automaticamente quatro aplicações comuns relacionadas com o Android Enterprise à consola de administração Intune. As quatro aplicações são as seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usado para Android Enterprise cenários totalmente geridos. Esta aplicação é automaticamente instalada em dispositivos totalmente geridos durante o processo de inscrição do dispositivo.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Ajuda-o a iniciar sessão nas suas contas se utilizar a verificação de dois fatores. Esta aplicação é automaticamente instalada em dispositivos totalmente geridos durante o processo de inscrição do dispositivo.
- **[Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usado para políticas de proteção de aplicações (APP) e cenários de perfil de trabalho Android Enterprise.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** - Usado para Android Enterprise dedicado cenários de quiosque multi-app. Os administradores de TI devem criar uma atribuição para instalar esta aplicação em dispositivos dedicados que serão usados em cenários de quiosque de várias aplicações.

>[!NOTE]
>Quando um utilizador final inscreve o seu dispositivo Android Enterprise totalmente gerido, a aplicação Intune Company Portal é instalada automaticamente e o ícone da aplicação pode ser visível para o utilizador final. Se o utilizador final tentar lançar a aplicação Intune Company Portal, o utilizador final será redirecionado para a aplicação Microsoft Intune e o ícone da aplicação Portal da Empresa será posteriormente ocultado.

## <a name="before-you-start"></a>Antes de começar
- Certifique-se de ter ligado o seu inquilino Intune ao Managed Google Play.  Para mais informações, consulte [Connect your Intune account to your Managed Google Play account](../enrollment/connect-intune-android-enterprise.md).
- Se pretender inscrever dispositivos de perfil de trabalho, certifique-se de ter configurado perfis de trabalho Intune e Android para trabalhar em conjunto na carga de trabalho de **inscrição** do Dispositivo do portal Azure. Para obter mais informações, veja [Inscrever dispositivos Android](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

## <a name="managed-google-play-app-types"></a>Tipos de aplicativos geridos do Google Play
Existem três tipos de aplicações que estão disponíveis com o Managed Google Play:

- **Aplicação gerida** pela Google Play Store - Aplicações públicas que estão geralmente disponíveis na Play Store. Gerencie estas aplicações em Intune, navegando para as aplicações que pretende gerir, aprovando-as e sincronizando-as em Intune.
- **Aplicação privada gerida** pelo Google Play - Estas são aplicações LOB publicadas para Managed Google Play by Intune admins.  Estas aplicações são privadas e estão disponíveis apenas para o seu inquilino Intune. É assim que as aplicações LOB são geridas e implementadas com o Managed Google Play e Android Enterprise.
- **Gerido google Play web link** - Web links com ícones definidos por administração de TI que são implementáveis para dispositivos Android Enterprise. Estes aparecem em dispositivos na lista de aplicações do dispositivo, tal como aplicações regulares.

## <a name="managed-google-play-store-apps"></a>Aplicativos geridos da Google Play store
Existem duas formas de navegar e aprovar aplicações geridas da Google Play store com intune:

1. Diretamente na consola Intune - navegue e aprove as aplicações da loja numa vista hospedada no Intune. Isto abre diretamente na consola Intune e não requer que se reatentie com uma conta diferente.
1. Na consola Gerida do Google Play - podes opcionalmente abrir a consola gerida do Google Play diretamente e aprovar aplicações lá. Consulte [sync a Managed Google Play app com Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune) para mais informações.  Isto requer um login separado utilizando a conta que usou para ligar o seu inquilino Intune ao Managed Google Play.

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Adicione uma aplicação gerida da Google Play store diretamente na consola Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo de aplicação Select,** nos tipos de **aplicações da Loja** disponíveis, selecione **aplicação Managed Google Play**.
4. Clique em **Selecionar**. A loja de aplicações **Managed Google Play** é apresentada.

    > [!NOTE]
    > A sua conta intune de inquilinos deve estar ligada à sua conta Android Enterprise para navegar nas aplicações geridas pela Google Play Store. Para mais informações, consulte [Connect your Intune account to your Managed Google Play account](../enrollment/connect-intune-android-enterprise.md).

5. Selecione uma aplicação para visualizar os detalhes da aplicação.
6. Na página que exibe a aplicação, clique em **Aprovar**. É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações.
7. Selecione **Aprovar** para aceitar as permissões da aplicação e continuar.
8. Selecione **Manter aprovado quando a aplicação solicitar novas permissões** no separador Definições de **Aprovação** e, em seguida, clicar **em Done**. 

    > [!IMPORTANT]
    > Se não escolher esta opção, terá de aprovar manualmente quaisquer novas permissões, caso o programador da aplicação publique uma atualização. Tal fará com que as instalações e atualizações da aplicação parem até que as permissões sejam aprovadas. Por este motivo, é recomendado selecionar a opção para aprovar automaticamente as novas permissões. 

9. Clique em **Selecionar** para selecionar a aplicação.
10. Clique em **Sync** na parte superior da lâmina para sincronizar a aplicação com o serviço Managed Google Play.
11. Clique em **Refresh** para atualizar a lista de aplicações e mostrar a aplicação recém-adicionada.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Adicione uma aplicação de loja gerida da Google Play na consola Gerida do Google Play (Alternativa)
Se preferir sincronizar uma aplicação do Managed Google Play com o Intune, em vez de a adicionar diretamente através do Intune, utilize os seguintes passos.

> [!IMPORTANT]
> As informações fornecidas abaixo são um método alternativo para adicionar uma aplicação do Managed Google Play através do Intune, conforme descrito acima.

1. Aceda à [Google Play Store Gerida](https://play.google.com/work). Inicie sessão com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
2. Procure na loja e selecione a aplicação que quer atribuir através do Intune.
3. Na página que exibe a aplicação, clique em **Aprovar**.  
    O seguinte exemplo mostra a aplicação Microsoft Excel escolhida.

    ![O botão Aprovar na Google Play Store Gerida](./media/apps-add-android-for-work/approve.png)

   É aberta uma janela da aplicação a pedir-lhe para dar permissões para a aplicação efetuar diversas operações.

4. Selecione **Aprovar** para aceitar as permissões da aplicação e continuar.

    ![O botão Aprovar das permissões de aplicações](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Selecione uma opção para processar novos pedidos de permissão de aplicações e, em seguida, selecione **Guardar**.

    ![Opções para processar novos pedidos de permissões de aplicações](./media/apps-add-android-for-work/approve-app-settings.png)

    A aplicação foi aprovada e é apresentada na consola de administração de TI. Em seguida, pode [sincronizar a aplicação](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune)de perfil de trabalho Android com Intune .

## <a name="managed-google-play-private-lob-apps"></a>Aplicativos geridos do Google Play privados (LOB)

Existem duas formas de adicionar aplicações LOB ao Managed Google Play:

1. Diretamente na consola Intune - Isto permite adicionar aplicações LOB, submetendo apenas a app APK e um título, diretamente dentro do Intune. Este método não requer que tenha uma conta de desenvolvimento do Google e não exige que pague a taxa para se registar na Google como desenvolvedor.  Este método é mais simples e tem um número significativamente reduzido de passos, e disponibiliza aplicações LOB para gestão em apenas dez minutos.
1. Na consola de desenvolvimento da Google Play - Se tiver uma conta de desenvolvimento da Google ou pretender configurar funcionalidades de distribuição avançadas que só estão disponíveis na Consola de Desenvolvimento de Google Play (como adicionar imagens adicionais de apps), pode utilizar a Consola de Desenvolvimento da [Google Play](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Aplicação privada (LOB) gerida do Google Play publicada diretamente na consola Intune

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo de aplicação Select,** nos tipos de **aplicações da Loja** disponíveis, selecione **aplicação Managed Google Play**.
4. Clique em **Selecionar**. A loja de aplicações **Managed Google Play** é apresentada dentro do Intune.
5. Selecione **aplicativos Privados** (ao lado do ícone de *bloqueio)* na janela Google Play. 
6. Clique no botão **"+"** na direita inferior para adicionar uma nova aplicação.
7. Adicione um **título** de aplicação e clique em **Upload APK** adicione o pacote de aplicações APK.
8. Clique em **Criar**.
9. Feche o painel managed Google Play se terminar de adicionar apps.
10. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play. 

    > [!NOTE]
    > As aplicações privadas podem demorar vários minutos a ficar disponíveis para sincronizar. Se a aplicação não aparecer na primeira vez que executa uma sincronização, aguarde alguns minutos e inicie uma nova sincronização.

Para obter mais informações sobre aplicações privadas geridas do Google Play, incluindo uma FAQ, consulte o artigo de suporte da Google: https://support.google.com/googleplay/work/answer/9146439

>[!IMPORTANT]
>As aplicações privadas adicionadas usando este método nunca podem ser tornadas públicas. Utilize apenas esta opção de publicação se tiver a certeza de que esta aplicação será sempre privada da sua organização.

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Aplicação gerida do Google Play privada (LOB) publicada usando a Consola de Desenvolvimento do Google

1. Inicie sessão na [Consola do Programador do Google Play](https://play.google.com/apps/publish) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.  
    Se estiver a iniciar sessão pela primeira vez, terá de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
2. Na consola, selecione **Adicionar nova aplicação**.
3. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)** .

    ![Apenas disponibilizar a aplicação para a sua organização](./media/apps-add-android-for-work/restrict.png)

    Esta operação disponibiliza a aplicação apenas para a sua organização. Não ficará disponível na Google Play Store pública.

    Para obter mais informações sobre como carregar e publicar aplicações Android, veja a [Ajuda da Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Depois de publicar a aplicação, inicie sessão na [loja do Managed Google Play](https://play.google.com/work) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
5. No nó **Aplicações** da loja, verifique se a aplicação que publicou é apresentada.  
    A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="managed-google-play-web-links"></a>Links web geridos do Google Play

As ligações web geridas pelo Google Play são instaladas e geríveis tal como outras aplicações Android. Quando instalados num dispositivo, aparecerão na lista de aplicações do utilizador ao lado das outras aplicações que instalaram. Quando filmados, serão lançados no navegador do dispositivo.

As ligações web serão abertas com o Microsoft Edge ou qualquer outra aplicação de navegador que escolha implementar. Certifique-se de que implementa pelo menos uma aplicação de navegador para dispositivos para que as ligações web possam abrir corretamente. No entanto, todas as opções de **Display** disponíveis para links web (ecrã completo, autónomo e UI mínimo) funcionarão apenas com o navegador Chrome. 

> [!IMPORTANT]
> A partir da publicação deste doc, existe um conhecido bug da Google que impede que as ligações web se abram em dispositivos com navegadores que não sejam o Chrome. A Google comprometeu-se a corrigir este bug.  Este aviso será removido quando a Microsoft tiver a confirmação de que a Google publicou a sua correção.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > **Todas as aplicações** > **Adicionar**.
3. No painel do **tipo de aplicação Select,** nos tipos de **aplicações da Loja** disponíveis, selecione **aplicação Managed Google Play**.
4. Clique em **Selecionar**. A loja de aplicações **Managed Google Play** é apresentada dentro do Intune.
5. Selecione **aplicações Web** (ao lado do ícone *Globe)* na janela Google Play.
6. Clique no botão **"+"** na direita inferior para adicionar uma nova aplicação.
7. Adicione uma aplicação **Title**, o **URL**da aplicação web, selecione como a aplicação deve ser exibida e selecione um ícone de aplicação.
8. Clique em **Criar**.
9. Feche o painel managed Google Play se terminar de adicionar apps.
10. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play. 

    > [!NOTE]
    > As aplicações web podem demorar vários minutos a ficar disponíveis para sincronizar. Se a aplicação não aparecer na primeira vez que executa uma sincronização, aguarde alguns minutos e inicie uma nova sincronização.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizar uma aplicação da Google Play Store Gerida com o Intune

Se aprovou uma aplicação da loja e não a vê na carga de trabalho das **Apps,** force uma sincronização imediata da seguinte forma:

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selecione **Apps** > **administração** de inquilinos > **Conectores e fichas** > **Managed Google Play**.
5. No painel **Google Play Gerido**, selecione **Atualizar**.  
    A página atualizará a hora e o estado da última sincronização.
6. No centro de administração do Microsoft Endpoint Manager selecione **Apps** > **Todas as aplicações**.  
    É apresentada a aplicação Google Play Store Gerida que ficou recentemente disponível.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos de perfil de trabalho do Android Enterprise

Quando a aplicação é exibida no nó de **licenças** da App do painel de **carga** de trabalho apps, pode [atribuí-la tal como atribuiria qualquer outra aplicação](/intune-azure/manage-apps/deploy-apps) atribuindo a app a grupos de utilizadores.

Depois de atribuir a aplicação, esta é instalada (ou disponível para instalação) nos dispositivos dos utilizadores a que tem como alvo. Não é pedida aprovação da instalação ao utilizador do dispositivo. Para obter mais informações sobre os dispositivos de perfil de trabalho do Android Enterprise, veja [Configurar a inscrição de dispositivos de perfil de trabalho do Android Enterprise](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Apenas as aplicações que foram atribuídas aparecerão na loja Managed Google Play para um utilizador final. Como tal, este é um passo fundamental para o administrador tomar na configuração de apps com o Managed Google Play.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos totalmente geridos do Android Enterprise

Os [dispositivos totalmente geridos do Android Enterprise](../enrollment/android-fully-managed-enroll.md) são dispositivos pertencentes à empresa associados a um único utilizador e utilizados exclusivamente para o trabalho e não para uso pessoal. Os utilizadores em dispositivos totalmente geridos podem obter as aplicações da empresa disponíveis na aplicação do Managed Google Play no dispositivo.

Por predefinição, um dispositivo totalmente gerido do Android Enterprise não permitirá que os funcionários instalem quaisquer aplicações que não sejam aprovadas pela organização. Além disso, os funcionários não poderão remover quaisquer aplicações instaladas que poderia ir contra a política. Se quiser permitir que os utilizadores acedam à Google Play Store completa para instalarem aplicações, em vez de terem acesso apenas a aplicações aprovadas na loja do Managed Google Play, poderá definir **Permitir o acesso a todas as aplicações na Google Play Store** como **Permitir**. Com esta definição, o utilizador pode aceder a todas as aplicações na Google Play Store com a conta empresarial, mas as compras podem ser limitadas. Pode remover a restrição de compras limitadas ao permitir que os utilizadores adicionem novas contas ao dispositivo. Se o fizer, permitirá que os utilizadores finais possam comprar aplicações na Google Play Store com as contas pessoais, bem como efetuar compras na aplicação. Para obter mais informações, veja [Definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades com o Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> A aplicação do Microsoft Intune e a aplicação do Microsoft Authenticator serão instaladas como aplicações necessárias em todos os dispositivos totalmente geridos durante a integração. Ter estas aplicações instaladas automaticamente fornece suporte de Acesso Condicional, e os utilizadores de aplicações Microsoft Intune podem ver e resolver problemas de conformidade. 

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

Para aplicações geridas do Google Play implementadas para dispositivos de perfil de trabalho Android Enterprise, pode ver o estado e o número de versão da aplicação instalada num dispositivo utilizando o Intune. 

## <a name="delete-managed-google-play-apps"></a>Eliminar aplicações do Managed Google Play
Quando necessário, pode eliminar as aplicações do Managed Google Play do Microsoft Intune. Para eliminar uma aplicação gerida pelo Google Play, abra o Microsoft Intune no portal Azure e selecione **Apps** > **Todas as aplicações.** Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

## <a name="android-enterprise-system-apps"></a>Aplicações do sistema Android Enterprise

Pode ativar um aplicativo de sistema Android Enterprise para [dispositivos dedicados](../enrollment/android-kiosk-enroll.md) ao Android Enterprise ou [dispositivos totalmente geridos.](../enrollment/android-fully-managed-enroll.md) Para obter mais informações sobre a adição de uma aplicação do sistema Android Enterprise, consulte adicionar aplicações do [sistema Android Enterprise ao Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Próximos passos

- [Atribuir aplicações a grupos](apps-deploy.md)
