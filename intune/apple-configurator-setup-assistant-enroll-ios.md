---
title: "Inscrever dispositivos iOS – Assistente de Configuração Apple Configurator"
titleSuffix: Intune on Azure
description: "Saiba como utilizar o Apple Configurator para inscrever dispositivos iOS pertencentes à empresa com o Assistente de Configuração.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Inscrever dispositivos iOS com o Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O Intune suporta a inscrição de dispositivos iOS pertencentes à empresa com o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) em execução num computador Mac. A inscrição com o Apple Configurator requer que ligue por USB cada dispositivo iOS a um computador Mac para configurar a inscrição empresarial. Pode inscrever dispositivos no Intune com o Apple Configurator de duas formas:
- **Inscrição com o Assistente de Configuração** – Realiza a reposição de fábrica do dispositivo, prepara-o para executar o Assistente de Configuração e instala as políticas da empresa para o novo utilizador do dispositivo. A maioria dos cenários exige que a política aplicada ao dispositivo iOS inclua afinidade de utilizador para ativar a aplicação Portal da Empresa do Intune.
- **Inscrição direta** – Não efetua a reposição de fábrica do dispositivo e inscreve o dispositivo com uma política predefinida. Este método destina-se a dispositivos **sem afinidade de utilizador**.

>[!NOTE]
>Este método de inscrição não pode ser utilizado com o método do [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](enrollment-method-choose-ios.md).

## <a name="prerequisites"></a>Pré-requisitos

Antes de configurar a inscrição de dispositivos iOS, tem de cumprir os seguintes pré-requisitos:

- [Um certificado push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Acesso físico a dispositivos iOS
- Números de série de dispositivos (veja [Como obter um número de série iOS](https://support.apple.com//HT204308))
- Cabos de ligação USB
- PC Mac com o [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Adicionar números de série do Apple Configurator](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>Inscrição através do Assistente de Configuração

### <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos. Os seguintes passos mostram como criar um perfil de inscrição de dispositivos para os dispositivos iOS inscritos através do Apple Configurator.

1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
2. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Perfis do AC**.
3. No painel **Perfis de Inscrição do Apple Configurator**, selecione **Criar**.
4. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.
5. Na **Afinidade de Utilizador**, escolha se os dispositivos com este perfil se vão inscrever com ou sem a afinidade do utilizador.

   - **Inscrever com afinidade do utilizador** – O dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, pode receber permissões para aceder ao e-mail e aos dados da empresa. A afinidade de utilizador deve ser configurada para dispositivos geridos que pertencem aos utilizadores e que precisam de utilizar o portal da empresa para serviços como a instalação de aplicações.
   - **Inscrever sem afinidade do utilizador** – O dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.

6. Selecione **Criar** para guardar o perfil.

### <a name="add-apple-configurator-serial-numbers"></a>Adicionar números de série do Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Utilize estes passos para adicionar números de série ao Intune quando pretende [inscrever dispositivos iOS da empresa ao utilizar o Apple Configurator com o Assistente de Configuração](apple-configurator-setup-assistant-enroll-ios.md). Pode adicionar números de série individualmente ou carregar um ficheiro de valores separados por vírgulas (CSV) de números de série. Depois de adicionar os números de série, pode atribuir-lhes um perfil. O perfil contém as definições de gestão específicas que quer aplicar aos dispositivos.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](enrollment-method-choose-ios.md).

**Para adicionar números de série do Apple Configurator ao Intune**

1. Crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o identificador IMEI na coluna da esquerda e os detalhes na coluna da direita. O máximo atual para a lista é de 500 linhas. Num editor de texto, a lista .csv tem um aspeto semelhante ao seguinte:

    F7TLWCLBX196,detalhes do serviço</br>
    DLXQPCWVGHMJ,detalhes do dispositivo

2. No portal do Azure, escolha **Inscrever dispositivos** e, em seguida, **Inscrição da Apple**.
3. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Números de Série do Apple Configurator**.
4. No painel **Números de Série do Apple Configurator**, selecione **Adicionar**.
5. No painel **Adicionar Números de Série**, selecione um perfil para aplicar os números de série que está a importar. Se estiver a importar um ficheiro com novos detalhes que vão substituir os existentes, selecione Substituir detalhes para os identificadores existentes para que os novos detalhes substituam os detalhes existentes.
6. Navegue para o ficheiro .csv dos números de série e selecione **Adicionar**.

### <a name="assign-a-profile-to-specific-serial-numbers"></a>Atribuir um perfil a números de série específicos

O Intune permite-lhe atribuir perfis a partir de dois locais diferentes no portal do Azure. Pode atribuir por perfil do Apple Configurator ou pode atribuir por dispositivos.

#### <a name="assign-by-devices"></a>Atribuir por dispositivos
1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
3. No painel **Dispositivos do Apple Configurator**, selecione os números de série aos quais pretende atribuir um perfil e, em seguida, selecione **Atribuir Perfil**.
4. No painel **Atribuir Perfil**, selecione o perfil que pretende atribuir e, em seguida, selecione **Atribuir**.

#### <a name="assign-by-profiles"></a>Atribuir por perfis
1. No portal do Intune, escolha **Inscrição de dispositivos** e, em seguida, **Inscrição da Apple**.
2. Escolha **Perfis do AC** e selecione o perfil ao qual pretende atribuir números de série.
3. No painel com o nome do perfil, selecione **Números de Série** > **Atribuir**.
4. Selecione os números de série que quer atribuir ao perfil e, em seguida, selecione o botão **Atribuir**.

### <a name="export-the-profile-to-ios-devices"></a>Exportar o perfil para dispositivos iOS
Depois de criar o perfil e atribuir números de série, terá de exportar o perfil do Intune, como um URL ou um ficheiro no formato descrito abaixo. Pode, então, importá-lo manualmente para o programa Apple Configurator num Mac. Em seguida, programa Apple Configurator implementa-o nos dispositivos.

1. No portal do Intune, selecione o painel **Perfis de Inscrição do Apple Configurator** e, em seguida, selecione o perfil a exportar.
2. No painel do perfil, selecione **Exportar Perfil**.
3. Copie o URL do perfil para o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12), com o dispositivo iOS ligado. Irá carregá-lo no Apple Configurator mais tarde para definir o perfil do Intune utilizado pelos dispositivos iOS.

  No procedimento seguinte, deverá carregar o URL deste perfil no serviço da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.
4. Carregue o URL deste perfil no serviço da Apple com o Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.
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

## <a name="direct-enrollment"></a>Inscrição direta
Quando inscreve diretamente dispositivos iOS com o Apple Configurator, pode inscrever um dispositivo sem adquirir o número de série do mesmo. Também pode dar um nome ao dispositivo para fins de identificação antes de o Intune capturar o nome do dispositivo durante a inscrição. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos diretamente. Esta instrução parte do princípio de que está a utilizar o Apple Configurator 2.0 no computador Mac.

1. No portal do Intune, escolha **Inscrição de dispositivos**, **Inscrição da Apple** e, em seguida, **Perfis do AC**.
2. No painel **Perfis de Inscrição do Apple Configurator**, selecione **Criar**.
3. No painel **Criar Perfil de Inscrição**, introduza um nome e uma descrição para o perfil.
4. Para **Afinidade de Utilizador**, escolha **Inscrever sem afinidade do utilizador** para garantir que o dispositivo não é afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar.
5. Selecione **Criar** para guardar o perfil.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportar o perfil como .mobileconfig para dispositivos iOS

1. No painel **Exportar Perfil**, transfira o perfil de inscrição para [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para emitir diretamente como um perfil de gestão para um dispositivo iOS ligado. Este método não faz uma reposição de fábrica do dispositivo.
2. Prepare o dispositivo com o Apple Configurator ao realizar os seguintes passos.
  1. Num computador Mac, abra o Apple Configurator 2.0.
  2. Ligue o dispositivo iOS ao computador Mac com um cabo USB. Feche Fotografias, o iTunes e outras aplicações que são abertas para o dispositivo quando o dispositivo é detetado.
  3. No Apple Configurator, selecione o dispositivo iOS ligado e, em seguida, selecione o botão **Adicionar**. As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente. Selecione **Perfis**.
  4. Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, selecione **Adicionar**. O perfil é adicionado ao dispositivo. Se o dispositivo for Não supervisionado, a instalação vai exigir a aceitação no dispositivo.
3. Realize os seguintes passos para instalar o perfil no dispositivo iOS. O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar. Se o registo implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque as implementações de aplicações irão exigir que tenha um ID Apple registado na App Store.
   1. Desbloqueie o dispositivo iOS.
   2. Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, escolha **Instalar**.
   3. Indique o Código de Acesso do Dispositivo ou o ID Apple, se for preciso.
   4. Aceite o **Aviso** e selecione **Instalar**.
   5. Aceite o **Aviso Remoto** e selecione **Confiar**.
   6. Quando a caixa **Perfil instalado** confirmar que o perfil foi Instalado, escolha **Concluído**.

    4. No dispositivo iOS, abra as **Definições** e aceda a **Geral** > **Gestão de Dispositivos** > **Perfil de Gestão**. Confirme que a instalação do perfil se encontra na lista e verifique as restrições de política do iOS e as aplicações instaladas. As restrições de política e as aplicações poderão demorar até 10 minutos a aparecer no dispositivo.

    5. Distribua os dispositivos. O dispositivo iOS está agora inscrito no Intune e gerido.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Como os utilizadores instalam e utilizam o Portal da Empresa nos dispositivos deles

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os dispositivos, têm de executar os passos adicionais descritos abaixo para concluir o Assistente de Configuração e instalar a aplicação Portal da Empresa.
