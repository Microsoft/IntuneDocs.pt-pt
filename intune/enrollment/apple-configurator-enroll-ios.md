---
title: registro de dispositivo iOS-Apple Configurator-assistente de configuração
titleSuffix: Microsoft Intune
description: Saiba como utilizar o Apple Configurator para inscrever dispositivos iOS pertencentes à empresa com o Assistente de Configuração.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21ee59af8c6d24a42ce3f8c9fefedd0e5dba7ba7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503319"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Configurar a inscrição de dispositivos iOS com o Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune suporta a inscrição de dispositivos iOS com o [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) em execução num computador Mac. A inscrição com o Apple Configurator requer que ligue por USB cada dispositivo iOS a um computador Mac para configurar a inscrição empresarial. Pode inscrever dispositivos no Intune com o Apple Configurator de duas formas:
- **Inscrição no Assistente de Configuração** – limpa o dispositivo e prepara-o para a inscrição durante o Assistente de Configuração.
- **Inscrição direta** – não efetua a limpeza do dispositivo e inscreve-o através das definições do iOS. Este método só suporta dispositivos **sem afinidade do utilizador**.

Os métodos de inscrição do Apple Configurator não podem ser utilizados com o [gestor de inscrições de dispositivos](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Pré-requisitos

- Acesso físico a dispositivos iOS
- [Definir autoridade MDM](../fundamentals/mdm-authority-set.md)
- [Um certificado push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Números de série dos dispositivos (apenas inscrição no Assistente de Configuração)
- Cabos de ligação USB
- Computador macOS a executar o [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de inscrição de dispositivos especifica as definições aplicadas durante a inscrição. Estas definições são aplicadas apenas uma vez. Siga estes passos para criar um perfil de inscrição para inscrever dispositivos iOS com o Apple Configurator.

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Perfis** > **Criar**.

    ![Criar um perfil para o Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. Em **Criar Perfil de Inscrição**, introduza um **Nome** e uma **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo Nome para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os grupos dinâmicos do Azure Active Directory.

    ![Captura de ecrã do ecrã Criar perfil com a opção Inscrever com afinidade do utilizador selecionada](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.

    - **Inscrever com afinidade do utilizador** – escolha esta opção para os dispositivos que pertençam aos utilizadores e que querem utilizar o portal da empresa para utilizar serviços como a instalação de aplicações. O dispositivo tem de ser afiliado a um utilizador com o Assistente de Configuração e, em seguida, pode aceder ao e-mail e aos dados da empresa. Só é suportada para a inscrição no Assistente de Configuração. A afinidade do utilizador necessita do [WS-Trust 1.3 Username/Mixed endpoint](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que realizem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores (incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio) não irão funcionar. Obrigatório para a inscrição direta.

     > [!NOTE]
     > Quando **registrar com afinidade de usuário** está selecionado, verifique se o dispositivo está afiliado a um usuário com o assistente de configuração nas primeiras 24 horas do dispositivo que está sendo registrado. Caso contrário, o registro pode falhar e uma redefinição de fábrica será necessária para registrar o dispositivo.

4. Se tiver escolhido **Inscrever com Afinidade do Utilizador**, tem a opção para permitir que os utilizadores se autentiquem com o Portal da Empresa em vez do Assistente de Configuração da Apple.

    > [!NOTE]
    > Se quiser realizar alguma das seguintes ações, defina **Autenticar com o Portal da Empresa em vez do Assistente de Configuração da Apple** para **Sim**.
    >    - utilizar a autenticação multifator
    >    - pedir aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez
    >    - Pedir aos utilizadores para reporem as respetivas palavras-passe expiradas durante a inscrição
    >
    > Estas ações não são suportadas durante a autenticação com o Assistente de Configuração da Apple.


6. Escolha **Criar** para guardar o perfil.

## <a name="setup-assistant-enrollment"></a>Inscrição através do Assistente de Configuração

### <a name="add-apple-configurator-serial-numbers"></a>Adicionar números de série do Apple Configurator

1. Crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o número de série na coluna da esquerda e os detalhes na coluna da direita. O máximo atual para a lista é de 5000 linhas. Num editor de texto, a lista .csv tem o seguinte aspeto:

    F7TLWCLBX196,detalhes do serviço</br>
    DLXQPCWVGHMJ,detalhes do dispositivo

   Saiba [como localizar o número de série de um dispositivo iOS](https://support.apple.com/HT204073).
2. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Dispositivos** > **Adicionar**.

5. Selecione um **Perfil de inscrição** para aplicar os números de série que está a importar. Se quiser que os detalhes do novo número de série substituam quaisquer detalhes existentes, escolha **Substituir os detalhes por identificadores existentes**.
6. Em **Importar Dispositivos**, procure o ficheiro csv de números de série e selecione **Adicionar**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Reatribuir um perfil a números de série de dispositivos

Pode atribuir um perfil de inscrição quando importar números de série iOS para a inscrição no Apple Configurator. Também pode atribuir perfis a partir de dois locais no portal do Azure:
- **Dispositivos do Apple Configurator**
- **Perfis de AC**

#### <a name="assign-from-apple-configurator-devices"></a>Atribuir a partir de dispositivos do Apple Configurator
1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Dispositivos** > escolha os números de série > **Atribuir perfil**.
2. Em **Atribuir Perfil**, escolha o **Novo perfil** que quer atribuir e, em seguida, escolha **Atribuir**.

#### <a name="assign-from-profiles"></a>Atribuir a partir de perfis
1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Perfis** > escolha um perfil.
2. No perfil, escolha **Dispositivos atribuídos** e, em seguida, escolha **Atribuir**.
3. Filtre para encontrar os números de série dos dispositivos que pretende atribuir ao perfil, selecione os dispositivos e, em seguida, selecione **Atribuir**.

### <a name="export-the-profile"></a>Exportar o perfil
Após criar o perfil e atribuir números de série, tem de exportar o perfil do Intune como um URL. Em seguida, importe-o para o Apple Configurator num Mac para implementar em dispositivos.

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Perfis** > escolha o perfil para exportar.
2. No perfil, selecione **Exportar Perfil**.
3. Copie o **URL do Perfil**. Em seguida, pode adicioná-lo ao Apple Configurator para definir o perfil do Intune utilizado pelos dispositivos iOS.

   Importe este perfil para o Apple Configurator no procedimento seguinte para definir o perfil do Intune utilizado pelos dispositivos iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Inscrever dispositivos com o Assistente de Configuração

1. Num computador Mac, abra o **Apple Configurator 2**. Na barra de menus, selecione **Apple Configurator 2** e selecione **Preferências**.
    > [!WARNING]
    > Os dispositivos são repostos para as configurações de fábrica durante o processo de inscrição. Como melhor prática, reponha o dispositivo e ligue-o. Os dispositivos deverão aparecer no ecrã **Hello** quando liga o dispositivo.
    > Se o dispositivo já foi registrado com a conta ID da Apple, o dispositivo deve ser excluído do iCloud da Apple antes de iniciar o processo de registro. O erro de prompt aparece como "não é possível ativar [nome do dispositivo]".

2. No painel **preferências**, selecione **Servidores** e selecione o símbolo de adição (+) para iniciar o assistente do Servidor MDM. Selecione **Next**.
3. Introduza o **Nome do anfitrião ou URL** e o **URL de inscrição** do servidor MDM em Inscrição do Assistente de Configuração para dispositivos iOS com Microsoft Intune. Para o URL de Inscrição, introduza o URL do perfil de inscrição exportado do Intune. Selecione **Next**.  
    Pode ignorar o aviso "URL do servidor não verificado" em segurança. Para continuar, selecione **Seguinte** até que o assistente esteja concluído.
4. Ligue os dispositivos móveis iOS ao computador Mac com um adaptador USB.
5. Selecione os dispositivos iOS que pretende gerir e, em seguida, selecione **Preparar**. No painel **Preparar o Dispositivo iOS**, selecione **Manual** e escolha **Seguinte**.
6. No painel **Inscrever no Servidor MDM**, selecione o nome do servidor que criou e escolha **Seguinte**.
7. No painel **Supervisionar Dispositivos**, selecione o nível de supervisão e, em seguida, selecione **Seguinte**.
8. No painel **Criar uma Organização**, escolha a **Organização** ou crie uma nova e escolha **Seguinte**.
9. No painel **Configurar Assistente de Configuração iOS**, escolha os passos a serem apresentados ao utilizador e, em seguida, escolha **Preparar**. Se lhe for pedido, autentique para atualizar as definições de fidedignidade.  
10. Quando concluir a preparação do dispositivo iOS, desligue o cabo USB.  

### <a name="distribute-devices"></a>Distribuir dispositivos
Os dispositivos estão agora prontos para a inscrição na empresa. Desligue os dispositivos e distribua-os pelos utilizadores. Quando os utilizadores ligarem os seus dispositivos, o Assistente de Configuração será iniciado.

Após os utilizadores receberem os dispositivos, os mesmos têm de concluir o Assistente de Configuração. Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos.

## <a name="direct-enrollment"></a>Inscrição direta
Quando inscreve diretamente dispositivos iOS com o Apple Configurator, pode inscrever um dispositivo sem adquirir o número de série do mesmo. Também pode dar um nome ao dispositivo para fins de identificação antes de o Intune capturar o nome do dispositivo durante a inscrição. A aplicação Portal da Empresa não é suportada para os dispositivos inscritos diretamente. Este método não apaga o dispositivo.

As aplicações que necessitam de afiliação de utilizadores, incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócios, não podem ser instaladas.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportar o perfil como .mobileconfig para dispositivos iOS

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Apple Configurator** > **Perfis** > escolha o perfil para exportar > **Exportar Perfil**.
2. Em **Inscrição direta**, escolha **Transferir perfil** e guarde o ficheiro. Um ficheiro de perfil de inscrição só é válido durante duas semanas e, após este período de tempo, terá de voltar a criá-lo.
3. Transfira o ficheiro para o computador Mac com o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para emitir diretamente como um perfil de gestão para dispositivos iOS.
4. Prepare o dispositivo com o Apple Configurator ao realizar os seguintes passos:
    1. Num computador Mac, abra o Apple Configurator 2.0.
    2. Ligue o dispositivo iOS ao computador Mac com um cabo USB. Feche Fotografias, o iTunes e outras aplicações que são abertas para o dispositivo quando o dispositivo é detetado.
    3. No Apple Configurator, selecione o dispositivo iOS ligado e, em seguida, selecione o botão **Adicionar**. As opções que podem ser adicionadas ao dispositivo aparecem na lista pendente. Selecione **Perfis**.

        ![Captura de ecrã da opção Exportar Perfil para a Inscrição no Assistente de Configuração com o URL do Perfil realçado](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Utilize o seletor de ficheiros para selecionar o ficheiro .mobileconfig que exportou a partir do Intune e, em seguida, selecione **Adicionar**. O perfil é adicionado ao dispositivo. Se o dispositivo for Não supervisionado, a instalação exige a aceitação no dispositivo.
5. Realize os seguintes passos para instalar o perfil no dispositivo iOS. O dispositivo já tem de ter concluído o Assistente de Configuração e estar pronto a utilizar. Se a inscrição implicar implementações de aplicações, o dispositivo deve ter um ID Apple configurado porque a implementação da aplicação exige que tenha um ID Apple registado na App Store.
    1. Desbloqueie o dispositivo iOS.
    2. Na caixa de diálogo **Instalar perfil** de **Perfil de gestão**, escolha **Instalar**.
    3. Indique o Código de Acesso do Dispositivo ou o ID Apple, se for necessário.
    4. Aceite o **Aviso** e selecione **Instalar**.
    5. Aceite o **Aviso Remoto** e selecione **Confiar**.
    6. Quando a caixa **Perfil instalado** confirmar que o perfil foi Instalado, escolha **Concluído**.

6. No dispositivo iOS, abra as **Definições** e aceda a **Geral** > **Gestão de Dispositivos** > **Perfil de Gestão**. Confirme que a instalação do perfil se encontra na lista e verifique as restrições de política do iOS e as aplicações instaladas. As restrições de política e as aplicações poderão demorar até 10 minutos a aparecer no dispositivo.

7. Distribua os dispositivos. O dispositivo iOS está agora inscrito no Intune e gerido.




