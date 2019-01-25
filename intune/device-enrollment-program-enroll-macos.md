---
title: Inscrever dispositivos macOS - programa de inscrição de dispositivos ou do Apple School Manager
titleSuffix: ''
description: Saiba como inscrever dispositivos macOS pertencentes à empresa através do Programa de Registo de Aparelho.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 064fa53341558ac18a228b56dca6d129cd58a3af
ms.sourcegitcommit: a30d4b699df4bff17ef39d6c93b2a5c5432db5ae
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54899081"
---
# <a name="automatically-enroll-macos-devices-with-the-device-enrollment-program-or-apple-school-manager"></a>Inscrever automaticamente dispositivos macOS com o programa de inscrição de dispositivos ou do Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode configurar a inscrição no Intune para dispositivos macOS adquiridas por meio da Apple [programa de inscrição de dispositivos (DEP)](https://deploy.apple.com) ou [Apple School Manager](https://school.apple.com/). Pode utilizar qualquer um dessas inscrições para um grande número de dispositivos sem sequer tocar nos mesmos. Pode enviar dispositivos macOS diretamente para os utilizadores. Quando o utilizador ativar o dispositivo, o Assistente de Configuração será executado com as predefinições configuradas e o dispositivo será inscrito na gestão do Intune.

Para configurar a inscrição, utilize os portais do Intune e do DEP da Apple. Criar perfis de inscrição com as definições aplicadas aos dispositivos durante a inscrição.

Nem a inscrição de DEP ou Apple School Manager funcionam com o [Gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos adquiridos através do [Apple School Manager](https://school.apple.com/) ou [programa de inscrição de dispositivos da Apple](http://deploy.apple.com)
- Uma lista de números de série ou um número de encomenda. 
- [Autoridade MDM](mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obter um token DEP da Apple

Antes de poder inscrever dispositivos macOS com o DEP ou Apple School Manager, precisa de um ficheiro de token (. p7m) do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos que sua organização é proprietária. Também permite que o Intune carregue perfis de inscrição para a Apple e para estes perfis nos dispositivos.

Utilize o portal da Apple para criar um token. Também utilizar o portal da Apple para atribuir dispositivos ao Intune para gestão.

> [!NOTE]
> Se eliminar o token a partir do portal clássico do Intune antes de migrar para o Azure, o Intune poderá restaurar um token de Apple eliminado. Pode eliminar novamente o token do portal do Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passo 1. Transfira o certificado de chave pública do Intune, que é obrigatório para criar o token.

1. No [portal do Azure no Intune](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

    ![Obtenha um token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro. pem é utilizado para pedir um certificado de relação de confiança a partir do portal da Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passo 2. Utilize a sua chave para transferir um token a partir da Apple.

1. Escolher **criar um token para o programa de inscrição de dispositivos da Apple** ou **criar um token através do Apple School Manager** para abrir o portal da Apple adequado e inicie sessão com a sua empresa ID Apple. Pode utilizar este ID Apple para renovar o token.
2.  Para o DEP, no portal da Apple, escolha **começar** para **o programa de inscrição de dispositivos** > **Manage Servers** > **adicionar MDM Servidor**.
3.  Para gerir de escola da Apple, no portal da Apple, escolha **servidores MDM** > **Adicionar servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
7. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Captura de ecrã a mostrar a especificação de dispositivos selecionados pelo número de série, a definição da ação de seleção como Atribuir ao servidor e a seleção do nome do servidor.](./media/enrollment-program-token-specify-serial.png)

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passo 3: Guardar o Apple ID que serviu para criar este token

No Intune no portal do Azure, forneça o ID Apple para referência futura.

![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Passo 4: Carregue o seu token.
Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos macOS ao enviar políticas para dispositivos inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token, escolha **Perfis** e, em seguida, escolha **Criar perfil**.

    ![Crie uma captura de ecrã de perfil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Em **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. Em **Plataforma**, selecione **macOS**.

5. Em **Afinidade de Utilizador**, escolha se os dispositivos com este perfil têm ou não de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade de Utilizador**: selecione esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar a aplicação Portal da Empresa para serviços como a instalação de aplicações. Se estiver a utilizar o Sistema de Ficheiros Distribuído do Azure, a afinidade de utilizador precisa de um [Nome de utilizador/Ponto final misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint). A autenticação multifator não é suportada para os dispositivos DEP de macOS com afinidade de utilizador.

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que realizem tarefas sem aceder aos dados de utilizador locais. As aplicações, como o Portal da Empresa, não funcionam.

6. Selecione **Definições de Gestão de Dispositivos** e escolha se quer ou não a inscrição bloqueada para dispositivos com este perfil. A **Inscrição bloqueada** desativa as definições do macOS que permitem que o perfil de gestão seja removido do menu **Preferências de Sistema** ou através do **Terminal**. Após a inscrição de dispositivos, não poderá alterar esta definição sem apagar os dados do dispositivo.

    ![Captura de ecrã a mostrar a opção Definições de Gestão de Dispositivos.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Escolha **OK**.

8. Selecione **Definições do Assistente de Configuração** para configurar as seguintes definições de perfil:  ![Personalização do Assistente de configuração.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | Definições do departamento | Descrição |
    |---|---|
    | <strong>Nome do Departamento</strong> | É apresentado quando os utilizadores tocam em <strong>Acerca da Configuração</strong> durante a ativação. |
    | <strong>Número de Telefone do Departamento</strong> | Aparece quando o utilizador clica no botão <strong>Preciso de Ajuda</strong> durante a ativação. |

  Pode optar por mostrar ou ocultar vários ecrãs do Assistente de Configuração no dispositivo quando o utilizador o configurar.
  - Se selecionar **Ocultar**, o ecrã não será apresentado durante a configuração. Depois de configurar o dispositivo, o utilizador ainda pode aceder ao menu **Definições** para configurar a funcionalidade.
  - Se selecionar **Mostrar**, o ecrã será apresentado durante a configuração. Por vezes, o utilizador pode ignorar o ecrã sem realizar qualquer ação. No entanto, terá a possibilidade de aceder ao menu **Definições** do dispositivo para configurar a funcionalidade. 


    | Definições do ecrã Assistente de Configuração | Se selecionar **Mostrar** durante a configuração, o dispositivo irá… |
    |------------------------------------------|------------------------------------------|
    | <strong>Código de Acesso</strong> | Pedir um código de acesso ao utilizador. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação). |
    | <strong>Serviços de Localização</strong> | Pedir ao utilizador a respetiva localização. |
    | <strong>Restaurar</strong> | Apresentar o ecrã **Aplicações e Dados**. Este ecrã permite que o utilizador opte por restaurar ou transferir os dados da Cópia de Segurança do iCloud quando configurar o dispositivo. |
    | <strong>iCloud e Apple ID</strong> | Apresentar ao utilizador as opções para iniciar sessão com o respetivo **ID Apple** e utilizar o **iCloud**.                         |
    | <strong>Termos e Condições</strong> | Pedir ao utilizador para aceitar os termos e condições da Apple. |
    | <strong>Touch ID</strong> | Apresentar ao utilizador a opção para configurar a identificação através de impressão digital no dispositivo. |
    | <strong>Apple Pay</strong> | Apresentar ao utilizador a opção para configurar o Apple Pay no dispositivo. |
    | <strong>Zoom</strong> | Apresentar ao utilizador a opção para aumentar o zoom quando este configurar o dispositivo. |
    | <strong>Siri</strong> | Apresentar ao utilizador a opção para configurar o Siri. |
    | <strong>Dados de Diagnóstico</strong> | Apresentar o ecrã **Diagnósticos** ao utilizador. Este ecrã permite que o utilizador opte por enviar dados de diagnóstico para a Apple. |
    | <strong>FileVault</strong> | Apresentar ao utilizador a opção de configurar a encriptação FileVault. |
    | <strong>Diagnóstico do iCloud</strong> | Apresentar ao utilizador a opção de enviar dados de diagnóstico do iCloud para a Apple. |
    | <strong>Registo</strong>| Pedir ao utilizador que registe o dispositivo. |
    | <strong>Migração de Android</strong> | Dar ao usuário a opção para migrar os dados de um dispositivo Android. |
    | <strong>Tom de apresentação</strong> | Dar ao usuário a opção para ativar o tom de exibição. |
    | <strong>Privacidade</strong> | Exiba a tela de privacidade para o usuário. |
    | <strong>Armazenamento do iCloud</strong> | Dar ao usuário a opção para utilizar o armazenamento do iCloud. |

   

10. Escolha **OK**.

11. Para guardar o perfil, escolha **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista > **Dispositivos** > **Sincronizar**. ![Captura de ecrã a mostrar o nó Dispositivos do Programa de Inscrição selecionado e a opção Sincronizar ligação a ser selecionada.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
   - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune obtém a lista atualizada completa de números de série atribuídos ao servidor de MDM da Apple ligado ao Intune. Depois de um dispositivo do Programa de Registo ser eliminado do portal do Intune sem a inscrição no servidor de MDM da Apple ser anulada no portal de DEP, o mesmo não voltará a ser importado para o Intune até a sincronização completa ser executada.   
   - É executa automaticamente uma sincronização a cada 24 horas. Também pode sincronizar ao clicar no botão **Sincronizar** (não mais do que uma vez a cada 15 minutos). Todos os pedidos de sincronização têm 15 minutos para serem concluídos. O botão **Sincronizar** está desativado até a sincronização ser concluída. Esta sincronização irá atualizar o estado do dispositivo existente e importar novos dispositivos atribuídos ao servidor de MDM da Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos**  >  **Inscrição da Apple**  >  **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos > **Atribuir**.

### <a name="assign-a-default-profile"></a>Atribuir um perfil predefinido

Pode escolher um perfil macOS e iOS predefinido a aplicar a todos os dispositivos que inscrever com um token específico. 

1. No Intune no portal do Azure, selecione **Inscrição de dispositivos** > **Inscrição da Apple**  >  **Tokens do programa de inscrição** > selecione um token na lista.
2. Escolha **Definir o Perfil Predefinido**, escolha um perfil na lista pendente e, em seguida, escolha **Guardar**. Este perfil será aplicado a todos os dispositivos inscritos com o token.

## <a name="distribute-devices"></a>Distribuir dispositivos
Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir que os dispositivos a inscrever. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Os dispositivos sem afinidade do utilizador necessitam de uma licença de dispositivo. Um dispositivo ativado não poderá aplicar um perfil de inscrição até que os dados do mesmo sejam apagados.

## <a name="renew-a-dep-token"></a>Renovar um token de DEP  
1. Aceda a deploy.apple.com.  
2. Em **Gerir Servidores**, selecione o servidor de MDM associado ao ficheiro de token que pretende renovar.
3. Selecione **Gerar Novo Token**.

    ![Captura de ecrã a mostrar a criação de um novo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Selecione **Token do Seu Servidor**.  
5. No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > selecione o token.
    ![Captura de ecrã a mostrar tokens de programas de inscrição.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Selecione **Renovar token** e introduza o ID Apple utilizado para criar o token original.  
    ![Captura de ecrã a mostrar a criação do novo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Carregue o token transferido recentemente.  
9. Selecione **Renovar token**. Verá a confirmação de que o token foi renovado.   
    ![Captura de ecrã a mostrar a confirmação.](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>Passos Seguintes

Depois de inscrever dispositivos macOS, pode começar a [geri-los](device-management.md).