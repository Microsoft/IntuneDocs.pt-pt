---
title: registro de dispositivo iOS-Apple Configurator-assistente de configuração
titleSuffix: Microsoft Intune
description: Saiba como usar o Apple Configurator para registrar dispositivos iOS de propriedade corporativa com o assistente de configuração.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1c2acc2ebe5528e30c344a31c9551ac64bdf3ca
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306780"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Configurar o registro de dispositivo iOS com o Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

O Intune dá suporte ao registro de dispositivos iOS usando o [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) em execução em um computador Mac. Registrar-se com o Apple Configurator exige que você conecte por USB cada dispositivo iOS a um computador Mac para configurar o registro corporativo. Você pode registrar dispositivos no Intune com o Apple Configurator de duas maneiras:
- **Registro do assistente de configuração** – apaga o dispositivo e o prepara para ser registrado durante o assistente de configuração.
- **Registro direto** – não apaga o dispositivo e registra o dispositivo por meio de configurações do Ios. Esse método só dá suporte a dispositivos sem **afinidade de usuário**.

Os métodos de registro do Apple Configurator não podem ser usados com o [Gerenciador de registro do dispositivo](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Pré-requisitos

- Acesso físico a dispositivos iOS
- [Definir autoridade de MDM](../fundamentals/mdm-authority-set.md)
- [Um Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)
- Números de série do dispositivo (somente registro do assistente de configuração)
- Cabos de conexão USB
- computador macOS executando o [Apple Configurator 2,0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Criar um perfil do Apple Configurator para dispositivos

Um perfil de registro de dispositivo define as configurações aplicadas durante o registro. Essas configurações são aplicadas apenas uma vez. Siga estas etapas para criar um perfil de registro para registrar dispositivos iOS com o Apple Configurator.

1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro da Apple** > **Apple configurator** > **perfis** > **criar**.

    ![Criar um perfil para o Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. Em **Criar perfil de registro**, digite um **nome** e uma **Descrição** para o perfil para fins administrativos. Os usuários não veem esses detalhes. Você pode usar esse campo de nome para criar um grupo dinâmico em Azure Active Directory. Use o nome do perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de registro. Saiba mais sobre Azure Active Directory grupos dinâmicos.

    ![Instantâneo da tela Criar perfil com o registro com afinidade do usuário selecionado](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. Para **afinidade de usuário**, escolha se os dispositivos com esse perfil devem ser registrados com ou sem um usuário atribuído.

    - **Registrar com afinidade do usuário** – escolha esta opção para dispositivos que pertencem a usuários e que desejam usar o portal da empresa para serviços como a instalação de aplicativos. O dispositivo deve ser afiliado a um usuário com o assistente de configuração e, em seguida, pode acessar dados e email da empresa. Somente com suporte para o registro do assistente de configuração. A afinidade do usuário requer o [ponto de extremidade/nome de usuário do WS-Trust 1,3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registrar sem afinidade do usuário** – escolha esta opção para dispositivos não afiliados com um único usuário. Use isso para dispositivos que executam tarefas sem acessar dados de usuário local. Aplicativos que exigem afiliação de usuário (incluindo o Portal da Empresa aplicativo usado para instalar aplicativos de linha de negócios) não funcionarão. Necessário para o registro direto.

     > [!NOTE]
     > Quando **registrar com afinidade de usuário** está selecionado, verifique se o dispositivo está afiliado a um usuário com o assistente de configuração nas primeiras 24 horas do dispositivo que está sendo registrado. Caso contrário, o registro pode falhar e uma redefinição de fábrica será necessária para registrar o dispositivo.

4. Se você escolher **registrar com afinidade de usuário**, terá a opção de permitir que os usuários se autentiquem com portal da empresa em vez do assistente de configuração da Apple.

    > [!NOTE]
    > Se você quiser fazer qualquer uma das ações a seguir, defina **autenticar com portal da empresa em vez do assistente de configuração da Apple** como **Sim**.
    >    - usar autenticação multifator
    >    - avisar os usuários que precisam alterar sua senha quando entrarem pela primeira vez
    >    - solicitar que os usuários redefinam suas senhas expiradas durante o registro
    >
    > Não há suporte para eles durante a autenticação com o assistente de configuração da Apple.


6. Escolha **criar** para salvar o perfil.

## <a name="setup-assistant-enrollment"></a>Registro do assistente de configuração

### <a name="add-apple-configurator-serial-numbers"></a>Adicionar números de série do Apple Configurator

1. Crie uma lista de duas colunas, valores separados por vírgulas (. csv) sem um cabeçalho. Adicione o número de série na coluna esquerda e os detalhes na coluna à direita. O máximo atual para a lista é de 5.000 linhas. Em um editor de texto, a lista. csv é parecida com esta:

    F7TLWCLBX196, detalhes do dispositivo</br>
    DLXQPCWVGHMJ, detalhes do dispositivo

   Saiba [como localizar um número de série do dispositivo IOS](https://support.apple.com/HT204073).
2. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro da Apple** > **Apple configurator** > **dispositivos** > **Adicionar**.

5. Selecione um **perfil de registro** para aplicar aos números de série que você está importando. Se desejar que os novos detalhes do número de série substituam os detalhes existentes, escolha **substituir detalhes para os identificadores existentes**.
6. Em **importar dispositivos**, navegue até o arquivo CSV de números de série e selecione **Adicionar**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Reatribuir um perfil aos números de série do dispositivo

Você pode atribuir um perfil de registro ao importar números de série do iOS para o registro do Apple Configurator. Você também pode atribuir perfis de dois locais na portal do Azure:
- **Dispositivos Apple Configurator**
- **Perfis de AC**

#### <a name="assign-from-apple-configurator-devices"></a>Atribuir de dispositivos Apple Configurator
1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro da Apple** > **Apple configurator** > **dispositivos** > escolha os números de série > **atribuir perfil**.
2. Em **atribuir perfil**, escolha o **novo perfil** que você deseja atribuir e, em seguida, escolha **atribuir**.

#### <a name="assign-from-profiles"></a>Atribuir de perfis
1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro da Apple** > **Apple configurator** > **perfis** > escolha um perfil.
2. No perfil, escolha **dispositivos atribuídos**e, em seguida, escolha **atribuir**.
3. Filtre para localizar os números de série do dispositivo que você deseja atribuir ao perfil, selecione os dispositivos e, em seguida, escolha **atribuir**.

### <a name="export-the-profile"></a>Exportar o perfil
Depois de criar o perfil e atribuir números de série, você deve exportar o perfil do Intune como uma URL. Em seguida, importe-o para o Apple Configurator em um Mac para implantação em dispositivos.

1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo**@no__t-**2 registro da Apple** > **perfis** **Apple Configurator** >  > escolha o perfil a ser exportado.
2. No perfil, selecione **exportar perfil**.
3. Copie a **URL do perfil**. Em seguida, você pode adicioná-lo no Apple Configurator para definir o perfil do Intune usado por dispositivos iOS.

   Em seguida, você importa esse perfil para o Apple Configurator no procedimento a seguir para definir o perfil do Intune usado por dispositivos iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Registrar dispositivos com o assistente de configuração

1. Em um computador Mac, abra o **Apple Configurator 2**. Na barra de menus, escolha **Apple Configurator 2**e, em seguida, escolha **preferências**.
    > [!WARNING]
    > Os dispositivos são redefinidos para configurações de fábrica durante o processo de registro. Como prática recomendada, redefina o dispositivo e ligue-o. Os dispositivos devem estar na tela de **saudação** quando você conectar o dispositivo.
    > Se o dispositivo já foi registrado com a conta ID da Apple, o dispositivo deve ser excluído do iCloud da Apple antes de iniciar o processo de registro. O erro de prompt aparece como "não é possível ativar [nome do dispositivo]".

2. No painel **preferências** , selecione **servidores** e escolha o símbolo de mais (+) para iniciar o assistente do servidor MDM. Escolha **Seguinte**.
3. Insira o **nome do host ou a URL** e a **URL de registro** para o servidor MDM em registro do assistente de configuração para dispositivos IOS com Microsoft Intune. Para a URL de registro, insira a URL do perfil de registro exportada do Intune. Escolha **Seguinte**.  
    Você pode desconsiderar com segurança um aviso informando "a URL do servidor não foi verificada". Para continuar, escolha **Avançar** até que o assistente seja concluído.
4. Conecte os dispositivos móveis iOS ao computador Mac com um adaptador USB.
5. Selecione os dispositivos iOS que você deseja gerenciar e, em seguida, escolha **preparar**. No painel **preparar o dispositivo IOS** , selecione **manual**e, em seguida, escolha **Avançar**.
6. No painel **registrar no servidor MDM** , selecione o nome do servidor que você criou e escolha **Avançar**.
7. No painel **supervisionar dispositivos** , selecione o nível de supervisão e, em seguida, escolha **Avançar**.
8. No painel **criar uma organização** , escolha a **organização** ou crie uma nova organização e, em seguida, escolha **Avançar**.
9. No painel **Configurar o assistente de configuração do IOS** , escolha as etapas a serem apresentadas ao usuário e escolha **preparar**. Se solicitado, autentique para atualizar as configurações de confiança.  
10. Quando o dispositivo iOS terminar a preparação, desconecte o cabo USB.  

### <a name="distribute-devices"></a>Distribuir dispositivos
Os dispositivos agora estão prontos para o registro corporativo. Desligue os dispositivos e distribua-os aos usuários. Quando os usuários ligam seus dispositivos, o assistente de configuração é iniciado.

Depois que os usuários recebem seus dispositivos, eles devem concluir o assistente de configuração. Dispositivos configurados com afinidade de usuário podem instalar e executar o aplicativo Portal da Empresa para baixar aplicativos e gerenciar dispositivos.

## <a name="direct-enrollment"></a>Registro direto
Ao registrar dispositivos iOS diretamente com o Apple Configurator, você pode registrar um dispositivo sem adquirir o número de série do dispositivo. Você também pode nomear o dispositivo para fins de identificação antes de o Intune capturar o nome do dispositivo durante o registro. Não há suporte para o aplicativo Portal da Empresa para dispositivos registrados diretamente. Esse método não apaga o dispositivo.

Os aplicativos que exigem a afiliação do usuário, incluindo o Portal da Empresa aplicativo usado para instalar aplicativos de linha de negócios, não podem ser instalados.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportar o perfil como. mobileconfig para dispositivos iOS

1. No [Intune](https://aka.ms/intuneportal), escolha **registro de dispositivo** > **registro da Apple** > **Apple configurator** > **perfis** > escolha o perfil para exportar > **perfil de exportação**.
2. Em **registro direto**, escolha **baixar perfil**e salve o arquivo. Um arquivo de perfil de registro só é válido por duas semanas no momento em que você deve recriá-lo.
3. Transfira o arquivo para um computador Mac executando o [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) para enviar por push diretamente como um perfil de gerenciamento para dispositivos IOS.
4. Prepare o dispositivo com o Apple Configurator usando as seguintes etapas:
    1. Em um computador Mac, abra o Apple Configurator 2,0.
    2. Conecte o dispositivo iOS ao computador Mac com um cabo USB. Feche fotos, iTunes e outros aplicativos que são abertos para o dispositivo quando o dispositivo é detectado.
    3. No Apple Configurator, escolha o dispositivo iOS conectado e, em seguida, escolha o botão **Adicionar** . As opções que podem ser adicionadas ao dispositivo aparecem na lista suspensa. Escolha **perfis**.

        ![Perfil de exportação de captura de tela para registro do assistente de configuração com URL de perfil](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Use o seletor de arquivos para selecionar o arquivo. mobileconfig que você exportou do Intune e escolha **Adicionar**. O perfil é adicionado ao dispositivo. Se o dispositivo estiver sem supervisão, a instalação do exigirá a aceitação no dispositivo.
5. Use as etapas a seguir para instalar o perfil no dispositivo iOS. O dispositivo já deve ter concluído o assistente de configuração e estar pronto para uso. Se o registro envolve as implantações de aplicativo, o dispositivo deve ter uma ID da Apple configurada porque a implantação do aplicativo requer que você tenha uma ID da Apple conectada para a loja de aplicativos.
    1. Desbloqueie o dispositivo iOS.
    2. Na caixa de diálogo **instalar perfil** para o **perfil de gerenciamento**, escolha **instalar**.
    3. Forneça a senha do dispositivo ou a ID da Apple, se necessário.
    4. Aceite o **aviso**e escolha **instalar**.
    5. Aceite o **aviso remoto**e escolha **confiar**.
    6. Quando a caixa **perfil instalado** confirmar o perfil como instalado, escolha **concluído**.

6. No dispositivo iOS, abra **configurações** e vá para @no__t **geral**-2**Gerenciamento de dispositivo** > **perfil de gerenciamento**. Confirme se a instalação do perfil está listada e verifique as restrições de política do iOS e os aplicativos instalados. As restrições de política e os aplicativos podem levar até 10 minutos para aparecer no dispositivo.

7. Distribua dispositivos. O dispositivo iOS agora está registrado no Intune e gerenciado.





