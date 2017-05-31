---
title: "Inscrever dispositivos iOS – Assistente de Configuração Apple Configurator"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Apple Configurator para inscrever dispositivos iOS pertencentes à empresa com o Assistente de Configuração."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e6b0bc51515a2b72c7574a7ca7e29c094f3bdbdb
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Inscrever dispositivos iOS com o Apple Configurator e o Assistente de configuração

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) em execução num computador Mac. Este processo realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

Através do Apple Configurator, pode repor um dispositivo iOS para as definições de fábrica e preparar a sua configuração para o novo utilizador do dispositivo. Este método requer que ligue o dispositivo iOS a um computador Mac através de USB para configurar a inscrição empresarial e parte do princípio de que está a utilizar o Apple Configurator 2.0. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua afinidade de utilizador para ativar a aplicação Portal da Empresa do Intune.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](enrollment-method-choose-ios.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos iOS, tem de cumprir os seguintes pré-requisitos:

- [Obter um certificado push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Confirmar que tem acesso físico aos dispositivos iOS
- Ter os números de série dos dispositivos (veja [Como obter um número de série iOS](https://support.apple.com//HT204308))
- Ter cabos de ligação USB disponíveis
- Confirmar que tem um PC Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) instalado
- [Adicionar números de série do Apple Configurator](apple-configurator-serial-numbers-add.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

3. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Perfis do AC**.

4. No painel **Perfis de Inscrição do Apple Configurator**, selecione **Criar**.

5. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.

6. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se vão inscrever com ou sem a afinidade do utilizador.

   - **Inscrever com afinidade do utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. A afinidade de utilizador deve ser configurada para dispositivos geridos que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações.

   - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

7. Selecione **Criar** para guardar o perfil.

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Atribuir números de série a um perfil do Apple Configurator

Depois de criar perfis do Apple Configurator, pode atribuir números de série de dispositivo aos perfis. Para poder atribuir números de série, primeiro tem de adicioná-los ao Intune ao seguir os passos em [Adicionar números de série do Apple Configurator](apple-configurator-serial-numbers-add.md).

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

  No procedimento seguinte, deverá carregar o URL deste perfil no serviço da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.

5. Carregue o URL deste perfil no serviço da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.
 1.  Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, selecione **Apple Configurator 2** e selecione **Preferências**.
  > [!WARNING]
  > Os dispositivos serão repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo.

  2. No painel **preferências**, selecione **Servidores** e selecione o símbolo de adição (+) para iniciar o assistente do Servidor MDM. Selecione **Seguinte**.

  3. Introduza o **Nome do anfitrião ou URL** e o **URL de inscrição** do servidor MDM em Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune. Selecione **Seguinte**.  

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

    Veja [Como dar formação aos seus utilizadores finais sobre o Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune). Também pode direcionar os utilizadores finais para [Utilizar o seu dispositivo iOS ou macOS com o Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os dispositivos, têm de executar os passos adicionais descritos abaixo para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.

