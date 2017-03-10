---
title: "Inscrever dispositivos iOS – Assistente de Configuração Apple Configurator"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Apple Configurator para inscrever dispositivos iOS pertencentes à empresa com o Assistente de Configuração."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b2d2e4e0210526ff70b86526bd0b2e17bab0286b
ms.lasthandoff: 02/18/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Inscrever dispositivos iOS com o Apple Configurator e o Assistente de configuração 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) em execução num computador Mac. Este processo realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](enroll-devices-using-device-enrollment-manager.md).

Através do Apple Configurator, pode repor um dispositivo iOS para as definições de fábrica e preparar a sua configuração para o novo utilizador do dispositivo. Este método requer que ligue o dispositivo iOS a um computador Mac através de USB para configurar a inscrição empresarial e parte do princípio de que está a utilizar o Apple Configurator 2.0. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua afinidade de utilizador para ativar a aplicação Portal da Empresa do Intune.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](choose-ios-enrollment-method.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos iOS, tem de cumprir os seguintes pré-requisitos:

- [Configurar domínios](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Definir a Autoridade de MDM](set-mdm-authority.md)
- [Criar grupos](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurar o Portal da Empresa](/intune-azure/manage-apps/company-portal-app.md)
- Atribuir licenças de utilizador no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obter um certificado push de MDM da Apple](get-an-apple-mdm-push-certificate.md)
- Confirmar que tem acesso físico aos dispositivos iOS
- Ter os números de série dos dispositivos (veja [Como obter um número de série iOS](https://support.apple.com//HT204308))
- Ter cabos de ligação USB disponíveis
- Confirmar que tem um PC Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) instalado
- [Adicionar números de série do Apple Configurator](add-apple-configurator-serial-numbers.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

3. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Perfis do AC**.

4. No painel **Perfis de Inscrição do Apple Configurator**, selecione **Criar**.

5. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.

6. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se vão inscrever com ou sem a afinidade do utilizador.

   - **Inscrever com afinidade do utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. A afinidade de utilizador deve ser configurada para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações.

   - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

7. Selecione **Criar** para guardar o perfil.

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Atribuir números de série a um perfil do Apple Configurator

Depois de criar perfis do Apple Configurator, pode atribuir números de série de dispositivo aos perfis. Para poder atribuir números de série, primeiro tem de adicioná-los ao Intune ao seguir os passos em [Adicionar números de série do Apple Configurator](add-apple-configurator-serial-numbers.md).

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>Atribuir números de série a perfis do Apple Configurator

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel **Perfis de Inscrição do Apple Configurator**, selecione o perfil ao qual quer atribuir números de série.

3. No painel com o nome do perfil, selecione **Números de Série** > **Atribuir**.

4. Selecione os números de série que quer atribuir ao perfil e, em seguida, selecione o botão **Atribuir**.

## <a name="export-the-profile-to-ios-devices"></a>Exportar o perfil para dispositivos iOS

Depois de criar o perfil e atribuir números de série, terá de exportar o perfil do Intune, como um URL ou um ficheiro no formato descrito abaixo. Pode, então, importá-lo manualmente para o programa Apple Configurator num Mac. Em seguida, programa Apple Configurator implementa-o nos dispositivos.

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>Exportar um perfil com a inscrição do Assistente de Configuração

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel **Perfis de Inscrição do Apple Configurator**, selecione o perfil a exportar.

3. No painel do perfil, selecione **Exportar Perfil**.

4. Copie o URL do perfil para o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12), com o dispositivo iOS ligado. Irá carregá-lo no Apple Configurator mais tarde para definir o perfil do Intune utilizado pelos dispositivos iOS.

  Para suportar o Apple Configurator 2, o URL do Perfil 2.0 tem de ser editado. Para tal, substitua este código:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Por este código:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   No procedimento seguinte, irá carregar o URL deste perfil para o serviço DEP da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.

5. Carregue o URL deste perfil para o serviço DEP da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.


    1.  Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, selecione **Apple Configurator 2** e selecione **Preferências**.

         > [!WARNING]
         > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo.

    2. No painel **preferências**, selecione **Servidores** e escolha o símbolo de adição (+) para iniciar o assistente do Servidor MDM. Selecione **Seguinte**.

    3. Introduza o **Nome** e o **URL de inscrição** para o servidor MDM do Passo n.º 6, em Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune. Selecione **Seguinte**.  

       Pode ignorar o aviso "URL do servidor não verificado" em segurança. Para continuar, selecione **Seguinte** até que o assistente esteja concluído.

    4.  Ligue os dispositivos móveis iOS ao computador Mac com um adaptador USB.

        > [!WARNING]
        > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando inicia o Assistente de Configuração.

    5.  Selecione **Preparar**. No painel **Preparar o Dispositivo iOS**, selecione **Manual** e selecione **Seguinte**.

    6. No painel **Inscrever no Servidor MDM**, selecione o nome do servidor que criou e escolha **Seguinte**.

    7. No painel **Supervisionar Dispositivos**, selecione o nível de supervisão e, em seguida, selecione **Seguinte**.

    8. No painel **Criar uma Organização**, escolha a **Organização** ou crie uma nova e escolha **Seguinte**.

    9. No painel **Configurar Assistente de Configuração iOS**, escolha os passos a serem apresentados ao utilizador e, em seguida, escolha **Preparar**. Se lhe for pedido, autentique para atualizar as definições de fidedignidade.  

    10. Quando concluir a preparação do dispositivo iOS, desligue o cabo USB.  

6.  **Distribua os dispositivos**.
    Os dispositivos estão agora prontos para a inscrição na empresa. Desligue os dispositivos e distribua-os pelos utilizadores. Quando os utilizadores ligarem os seus dispositivos, o Assistente de Configuração será iniciado.

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os dispositivos, têm de executar os passos adicionais descritos abaixo para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador

1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. Durante a configuração, os utilizadores recebem um pedido de credenciais. Terão de utilizar as credenciais (ou seja, o nome pessoal exclusivo ou UPN) associadas à subscrição no Intune.

2. Durante a configuração, os utilizadores recebem um pedido do Apple ID. Terão de fornecer um Apple ID para permitir que o dispositivo instale o Portal da Empresa. Também podem fornecer o ID no menu de definições do iOS após a conclusão da configuração.

3. Depois de concluir a configuração, o dispositivo iOS tem de instalar a aplicação Portal da Empresa a partir da App Store.

4. O utilizador poderá então iniciar sessão no Portal da Empresa através do UPN utilizado quando configurou o dispositivo.

5. Após iniciar sessão, é pedido aos utilizadores que inscrevam o dispositivo. O primeiro passo consiste em identificar o dispositivo. A aplicação apresenta uma lista de dispositivos iOS que já foram inscritos pela empresa e atribuídos à conta do Intune do utilizador. Deve escolher o dispositivo correspondente. Se este dispositivo ainda não tiver sido inscrito pela empresa, deverão escolher um novo dispositivo para continuar o fluxo de inscrição padrão.

6. No ecrã seguinte, os utilizadores têm de confirmar o número de série do novo dispositivo. Os utilizadores podem tocar na ligação confirme o Número de Série para iniciar a aplicação Definições e verificar o número de série. Em seguida, os utilizadores têm de introduzir os últimos quatro carateres do número de série na aplicação Portal da Empresa.

    Este passo verifica se o dispositivo é o dispositivo da empresa inscrito no Intune. Se o número de série do dispositivo não coincidir, significa que foi selecionado o dispositivo errado. O utilizador deve voltar ao ecrã anterior e selecionar um dispositivo diferente.

7. Depois de verificar o número de série, a aplicação Portal da Empresa redireciona o utilizador para o site do Portal da Empresa para finalizar a inscrição. Em seguida, o site solicita aos utilizadores que voltem para a aplicação.

A inscrição está concluída e os utilizadores podem utilizar este dispositivo com o conjunto completo de capacidades.

