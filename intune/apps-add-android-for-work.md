---
title: Atribuir aplicações do Managed Google Play a dispositivos Android Enterprise
titleSuffix: Microsoft Intune
description: Saiba como sincronizar e atribuir aplicações a dispositivos Android Enterprise a partir da loja do Managed Google Play.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: da1ee116d66fff3b244a1231c311adceeb72df85
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304243"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Adicionar aplicações do Managed Google Play a dispositivos Android Enterprise com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A Google Play gerenciada é a Enterprise App Store do Google e a única fonte de aplicativos para Android Enterprise. Você pode usar o Intune para orquestrar a implantação de aplicativos por meio de Google Play gerenciados para qualquer cenário do Android Enterprise (incluindo o perfil de trabalho, os registros dedicados e totalmente gerenciados). A maneira como você adiciona aplicativos gerenciados Google Play ao Intune difere de como os aplicativos Android são adicionados ao não Android Enterprise. Aplicativos da loja, aplicativos de linha de negócios (LOB) e aplicativos Web são aprovados ou adicionados ao Google Play gerenciado e, em seguida, sincronizados no Intune para que eles apareçam na lista de aplicativos cliente. Depois que eles aparecerem na lista de lista de aplicativos cliente, você poderá gerenciar a atribuição de qualquer aplicativo Google Play gerenciado como faria com qualquer outro aplicativo.

Para facilitar a configuração e o uso do gerenciamento corporativo do Android, ao conectar seu locatário do Intune ao Google Play gerenciado, o Intune adicionará automaticamente quatro aplicativos comuns do Android Enterprise ao console de administração do Intune. Os quatro aplicativos são os seguintes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** -usados para cenários totalmente gerenciados do Android Enterprise. Esse aplicativo é instalado automaticamente em dispositivos totalmente gerenciados durante o processo de registro do dispositivo.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -ajuda você a entrar em suas contas se usar a verificação de dois fatores. Esse aplicativo é instalado automaticamente em dispositivos totalmente gerenciados durante o processo de registro do dispositivo.
- **[Portal da empresa do Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** -usado para as políticas de proteção de aplicativo (aplicativo) e cenários de perfil de trabalho do Android Enterprise.
- **[Tela inicial gerenciada](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** -usada para cenários de quiosque de vários aplicativos dedicados ao Android Enterprise. Os administradores de ti devem criar uma atribuição para instalar esse aplicativo em dispositivos dedicados que serão usados em cenários de quiosque de vários aplicativos.

>[!NOTE]
>Quando um usuário final registra seu dispositivo Android Enterprise totalmente gerenciado, o aplicativo Portal da Empresa do Intune é instalado automaticamente e o ícone do aplicativo pode estar visível para o usuário final. Se o usuário final tentar iniciar o aplicativo Portal da Empresa do Intune, o usuário final será redirecionado para o aplicativo Microsoft Intune e o ícone do aplicativo Portal da Empresa será subsequentemente oculto.

## <a name="before-you-start"></a>Antes de começar
- Verifique se você conectou seu locatário do Intune ao Google Play gerenciado.  Para obter mais informações, consulte [conectar sua conta do Intune à sua conta do Google Play gerenciado](connect-intune-android-enterprise.md).
- Se você pretende registrar dispositivos de perfil de trabalho, verifique se configurou os perfis de trabalho do Intune e do Android para trabalhar juntos na carga de trabalhos de **registro do dispositivo** do portal do Azure. Para obter mais informações, veja [Inscrever dispositivos Android](android-work-profile-enroll.md).

>[!NOTE]
>Ao trabalhar com o Microsoft Intune, recomendamos que utilize o browser Microsoft Edge ou Google Chrome.

## <a name="managed-google-play-app-types"></a>Tipos de aplicativo Google Play gerenciados
Há três tipos de aplicativos que estão disponíveis com Google Play gerenciados:

* **Aplicativo gerenciado do Google Play Store** -aplicativos públicos que estão geralmente disponíveis no Play Store. Gerencie esses aplicativos no Intune procurando os aplicativos que você deseja gerenciar, aprovando-os e, em seguida, sincronizando-os no Intune.
* **Aplicativo gerenciado Google Play privado** -esses são aplicativos LOB publicados para Google Play gerenciados pelos administradores do Intune.  Esses aplicativos são privados e estão disponíveis somente para seu locatário do Intune. É assim que os aplicativos LOB são gerenciados e implantados com o Google Play gerenciado e o Android Enterprise.
* **Link da Web do Google Play gerenciado** -links da Web com ícones definidos pelo administrador de ti que são implantáveis em dispositivos Android Enterprise. Eles aparecem em dispositivos na lista de aplicativos do dispositivo, assim como aplicativos regulares.

## <a name="managed-google-play-store-apps"></a>Aplicativos gerenciados da Store Google Play
Há duas maneiras de procurar e aprovar aplicativos gerenciados da Google Play Store com o Intune:

1. Diretamente no console do Intune – Navegue e aprove aplicativos da loja em uma exibição hospedada no Intune. Isso é aberto diretamente no console do Intune e não exige a reautenticação com uma conta diferente.
1. No console gerenciado Google Play-você pode opcionalmente abrir o console do Google Play gerenciado diretamente e aprovar os aplicativos. Consulte [sincronizar um aplicativo gerenciado Google Play com o Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune) para obter mais informações.  Isso requer um logon separado usando a conta que você usou para conectar seu locatário do Intune ao Google Play gerenciado.


### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Adicionar um aplicativo gerenciado da Store Google Play diretamente no console do Intune

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações cliente** > **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na caixa pendente **Tipo de aplicação**, selecione **Managed Google Play**.
7. Selecione **Google Play gerenciado-abrir** para abrir o catálogo de Google Play gerenciado.
7. Selecione **pesquisar Play Store** no catálogo de Google Play.
8. Use a caixa de pesquisa para procurar aplicativos que você deseja gerenciar.
9. Clique em **Aprovar** para aprovar a aplicação no Managed Google Play e clique em **Aprovar** para aceitar as permissões da aplicação.
10. Selecione **Manter aprovado quando as aplicações pedirem novas permissões** na janela Definições de Aprovação e, em seguida, clique em **Guardar**. Se não escolher esta opção, terá de aprovar manualmente quaisquer novas permissões, caso o programador da aplicação publique uma atualização. Tal fará com que as instalações e atualizações da aplicação parem até que as permissões sejam aprovadas. Por este motivo, é recomendado selecionar a opção para aprovar automaticamente as novas permissões. 
11. Clique em **OK** para incluir a aplicação (ou aplicações) que aprovou.
12. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Adicionar um aplicativo gerenciado da Store Google Play no console do Google Play gerenciado (alternativa)
Se preferir sincronizar uma aplicação do Managed Google Play com o Intune, em vez de a adicionar diretamente através do Intune, utilize os seguintes passos.

> [!IMPORTANT]
> As informações fornecidas abaixo são um método alternativo para adicionar uma aplicação do Managed Google Play através do Intune, conforme descrito acima.

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

    A aplicação foi aprovada e é apresentada na consola de administração de TI. Em seguida, você pode [sincronizar o aplicativo de perfil de trabalho do Android com o Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>Aplicativos gerenciados de Google Play privada (LOB)

Há duas maneiras de adicionar aplicativos LOB a Google Play gerenciados:

1. Diretamente no console do Intune – isso permite que você adicione aplicativos LOB enviando apenas o aplicativo APK e um título, diretamente no Intune. Esse método não exige que você tenha uma conta de desenvolvedor do Google e não exija que você pague a taxa para registrar-se no Google como desenvolvedor.  Esse método é mais simples e tem um número significativamente reduzido de etapas e torna os aplicativos LOB disponíveis para gerenciamento em até dez minutos.
1. No console do desenvolvedor do Google Play-se você tiver uma conta de desenvolvedor do Google ou desejar configurar recursos de distribuição avançada que só estão disponíveis no console do desenvolvedor Google Play (como adicionar capturas de tela de aplicativo adicionais), você poderá usar o [Google Play Console do desenvolvedor](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Publicação de aplicativo de LOB (Google Play privada) gerenciada diretamente no console do Intune

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações cliente** > **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na caixa pendente **Tipo de aplicação**, selecione **Managed Google Play**.
7. Selecione **Google Play gerenciado-abrir** para abrir o catálogo de Google Play gerenciado.
7. Selecione **aplicativos privados** no catálogo de Google Play.
7. Clique no botão **"+"** para adicionar um novo aplicativo
8. Enviar um título de aplicativo e um pacote APK para o aplicativo
9. Clique em **Criar**
9. Feche o painel de Google Play gerenciado se você tiver terminado de adicionar aplicativos
12. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play. Observe que os aplicativos privados podem levar vários minutos para ficarem disponíveis para sincronização. Se não aparecer na primeira vez em que você executar uma sincronização, aguarde alguns minutos e inicie uma nova sincronização.

Para obter mais informações sobre aplicativos gerenciados Google Play particulares, incluindo perguntas frequentes, consulte o artigo de suporte do Google: https://support.google.com/googleplay/work/answer/9146439

>[!NOTE]
>Aplicativos privados adicionados usando esse método nunca podem ser tornados públicos. Use esta opção de publicação somente se você tiver certeza de que esse aplicativo será sempre privado para sua organização.
  

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Publicação de aplicativo de LOB (Google Play privada) gerenciada usando o console do desenvolvedor do Google

1. Inicie sessão na [Consola do Programador do Google Play](https://play.google.com/apps/publish) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.  
    Se estiver a iniciar sessão pela primeira vez, terá de se registar e pagar uma taxa para se tornar um membro do programa Google Developer.
2. Na consola, selecione **Adicionar nova aplicação**.
3. Deve carregar e fornecer informações sobre a sua aplicação da mesma forma que publica qualquer aplicação na Google Play Store. No entanto, tem de selecionar a definição **Apenas disponibilizar esta aplicação para a minha organização (<*nome da organização*>)** .

    ![Apenas disponibilizar a aplicação para a sua organização](media/restrict.png)

    Esta operação disponibiliza a aplicação apenas para a sua organização. Não ficará disponível na Google Play Store pública.

    Para obter mais informações sobre como carregar e publicar aplicações Android, veja a [Ajuda da Google Developer Console](https://support.google.com/googleplay/android-developer/answer/113469).
4. Depois de publicar a aplicação, inicie sessão na [loja do Managed Google Play](https://play.google.com/work) com a mesma conta que utilizou para configurar a ligação entre o Intune e o Android Enterprise.
5. No nó **Aplicações** da loja, verifique se a aplicação que publicou é apresentada.  
    A aplicação é automaticamente aprovada para ser sincronizada com o Intune.

## <a name="managed-google-play-web-links"></a>Links da Web Google Play gerenciados

Os links da Web gerenciados Google Play são instaláveis e gerenciáveis da mesma forma que outros aplicativos Android. Quando instalado em um dispositivo, ele será exibido na lista de aplicativos do usuário junto com os outros aplicativos que eles instalaram. Quando tocadas, eles serão iniciados no navegador do dispositivo.

Os links da Web serão abertos com o Microsoft Edge ou qualquer outro aplicativo de navegador que você escolher implantar. Certifique-se de implantar pelo menos um aplicativo de navegador para dispositivos a fim de que os links da Web possam ser abertos corretamente. No entanto, todas as opções de **exibição** disponíveis para links da Web (tela inteira, autônoma e interface do usuário mínima) só funcionarão com o navegador Chrome. 

> [!IMPORTANT]
> A partir da publicação deste documento, há um Google bug conhecido que impede que os links da Web sejam abertos em dispositivos com navegadores diferentes do Chrome. O Google se comprometeu em corrigir esse bug.  Esse aviso será removido quando a Microsoft confirmar que o Google publicou sua correção.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações cliente** > **Aplicações**.
5. No painel **Aplicações**, selecione **Adicionar**.
6. Na caixa pendente **Tipo de aplicação**, selecione **Managed Google Play**.
7. Selecione **Google Play gerenciado-abrir** para abrir o catálogo de Google Play gerenciado.
7. Selecione **aplicativos Web** no catálogo Google Play.
7. Clique no botão **"+"** para adicionar um novo aplicativo
7. Insira as informações necessárias e clique em **criar**
7. Feche o painel de Google Play gerenciado se você tiver terminado de adicionar aplicativos
12. Clique em **Sincronizar** no painel **Aplicação** para sincronizar com o serviço Managed Google Play. Observe que os aplicativos privados podem levar vários minutos para ficarem disponíveis para sincronização. Se não aparecer na primeira vez em que você executar uma sincronização, aguarde alguns minutos e inicie uma nova sincronização.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Sincronizar uma aplicação da Google Play Store Gerida com o Intune

Se você aprovou um aplicativo da loja e não o vê na carga de trabalho **aplicativos cliente** , Force uma sincronização imediata da seguinte maneira:

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Aplicações do cliente**.
4. No painel de carga de trabalho **Aplicações do cliente**, em **Configuração**, selecione **Google Play Gerido**.
5. No painel **Google Play Gerido**, selecione **Atualizar**.  
    A página atualizará a hora e o estado da última sincronização.
6. No painel de carga de trabalho **Aplicações do cliente**, selecione **Aplicações**.  
    É apresentada a aplicação Google Play Store Gerida que ficou recentemente disponível.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos de perfil de trabalho do Android Enterprise

Quando o aplicativo é exibido no nó **licenças de aplicativos** do painel de carga de trabalho **aplicativos cliente** , você pode [atribuí-lo da mesma forma que atribuiria qualquer outro aplicativo](/intune-azure/manage-apps/deploy-apps) , atribuindo o aplicativo a grupos de usuários.

Depois de atribuir o aplicativo, ele é instalado (ou disponível para instalação) nos dispositivos dos usuários que você tiver direcionado. Não é pedida aprovação da instalação ao utilizador do dispositivo. Para obter mais informações sobre os dispositivos de perfil de trabalho do Android Enterprise, veja [Configurar a inscrição de dispositivos de perfil de trabalho do Android Enterprise](android-work-profile-enroll.md). 

> [!NOTE] 
> Somente os aplicativos que foram atribuídos serão exibidos no repositório de Google Play gerenciado para um usuário final. Dessa forma, essa é uma etapa importante para o administrador realizar ao configurar aplicativos com Google Play gerenciados.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Atribuir uma aplicação do Managed Google Play aos dispositivos totalmente geridos do Android Enterprise

Os [dispositivos totalmente geridos do Android Enterprise](android-fully-managed-enroll.md) são dispositivos pertencentes à empresa associados a um único utilizador e utilizados exclusivamente para o trabalho e não para uso pessoal. Os utilizadores em dispositivos totalmente geridos podem obter as aplicações da empresa disponíveis na aplicação do Managed Google Play no dispositivo.

Por predefinição, um dispositivo totalmente gerido do Android Enterprise não permitirá que os funcionários instalem quaisquer aplicações que não sejam aprovadas pela organização. Além disso, os funcionários não poderão remover quaisquer aplicações instaladas que poderia ir contra a política. Se quiser permitir que os utilizadores acedam à Google Play Store completa para instalarem aplicações, em vez de terem acesso apenas a aplicações aprovadas na loja do Managed Google Play, poderá definir **Permitir o acesso a todas as aplicações na Google Play Store** como **Permitir**. Com esta definição, o utilizador pode aceder a todas as aplicações na Google Play Store com a conta empresarial, mas as compras podem ser limitadas. Pode remover a restrição de compras limitadas ao permitir que os utilizadores adicionem novas contas ao dispositivo. Se o fizer, permitirá que os utilizadores finais possam comprar aplicações na Google Play Store com as contas pessoais, bem como efetuar compras na aplicação. Para obter mais informações, veja [Definições de dispositivos Android Enterprise para permitir ou restringir funcionalidades com o Intune](device-restrictions-android-for-work.md). 

> [!NOTE]
> A aplicação do Microsoft Intune e a aplicação do Microsoft Authenticator serão instaladas como aplicações necessárias em todos os dispositivos totalmente geridos durante a integração. Ter esses aplicativos instalados automaticamente fornece suporte de acesso condicional e Microsoft Intune os usuários do aplicativo podem ver e resolver problemas de conformidade. 

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


## <a name="delete-managed-google-play-apps"></a>Eliminar aplicações do Managed Google Play
Quando necessário, pode eliminar as aplicações do Managed Google Play do Microsoft Intune. Para eliminar uma aplicação do Managed Google Play, abra o Microsoft Intune no portal do Azure e selecione **Aplicações cliente** > **Aplicações**. Na lista de aplicações, selecione as reticências (...) à direita da aplicação do Managed Google Play e, em seguida, selecione **Eliminar** na lista apresentada. Quando elimina uma aplicação do Managed Google Play da lista de aplicações, essa aplicação passa automaticamente a não aprovada.

## <a name="android-enterprise-system-apps"></a>Aplicações do sistema Android Enterprise

Você pode habilitar um aplicativo Android Enterprise System para [dispositivos Android Enterprise dedicados](android-kiosk-enroll.md) ou [dispositivos totalmente gerenciados](android-fully-managed-enroll.md). Para obter mais informações sobre como adicionar um aplicativo Android Enterprise System, consulte [adicionar aplicativos do Android Enterprise System ao Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Passos seguintes

- [Atribuir aplicações a grupos](apps-deploy.md)
