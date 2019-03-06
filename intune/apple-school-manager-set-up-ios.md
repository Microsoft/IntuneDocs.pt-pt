---
title: Inscrição do programa do Apple School Manager para dispositivos iOS
titleSuffix: Microsoft Intune
description: Saiba como configurar a inscrição do programa do Apple School Manager para dispositivos iOS da empresa com o Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d99712cfb972ae346c9254aac54feb5f4173a28
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57390305"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Configurar a inscrição de dispositivos iOS com o Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pode configurar o Intune para inscrever dispositivos iOS adquiridos através do [Apple School Manager](https://school.apple.com/) programa. Ao utilizar o Intune com o Apple School Manager, pode inscrever um grande número de dispositivos iOS sem sequer tocar nos mesmos. Quando um estudante ou professor ativar o dispositivo, o Assistente de Configuração é executado com as predefinições configuradas e o dispositivo é inscrito para gestão.

Para ativar a inscrição do Apple School Manager, utilize os portais do Intune e do Apple School Manager. É necessária uma lista de números de série ou um número de encomenda para poder atribuir dispositivos ao Intune para gestão. São criados os perfis de inscrição DEP com as definições aplicadas aos dispositivos durante a inscrição.

Não pode utilizar a inscrição do Apple School Manager com o [Programa de Registo de Aparelho da Apple](device-enrollment-program-enroll-ios.md) nem com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

**Pré-requisitos**
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- [Autoridade MDM](mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)
- Se estiver a utilizar o Sistema de Ficheiros Distribuído do Azure, a afinidade de utilizador precisa de um [Nome de utilizador/Ponto final misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Dispositivos comprados a partir do programa [Apple School Manager](http://school.apple.com)

## <a name="get-an-apple-token-and-assign-devices"></a>Obter um token da Apple e atribuir dispositivos

Para poder inscrever dispositivos iOS da empresa através do Apple School Manager, precisa de ter um ficheiro de token (.p7m) da Apple. Este token permite que o Intune sincronize as informações sobre os dispositivos que participam no Apple School Manager. Também permite ao Intune efetuar carregamentos do perfil de inscrição para a Apple e atribuir dispositivos a esses perfis. Enquanto estiver no portal da Apple, também pode atribuir números de série de dispositivos para gerir.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Passo 1. Transfira o certificado de chave pública do Intune, que é obrigatório para criar um token da Apple

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > **Adicionar**.

   ![Obtenha um token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image01.png)

2. No painel **Token do programa de inscrição**, selecione **Transfira a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Apple School Manager.
     ![Painel Token do Programa de Inscrição.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Passo 2. Transferir um token e atribuir dispositivos
1. Escolha **Criar um token através do Apple School Manager** e inicie sessão no Apple School com o Apple ID da sua empresa. Pode utilizar este ID Apple para renovar o seu token do Apple School Manager.
2.  No [portal do Apple School Manager](https://school.apple.com), aceda a **Servidores MDM** e, em seguida, selecione **Adicionar Servidor MDM** (canto superior direito).
3.  Introduza o **Nome do Servidor MDM**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.
   ![Captura de ecrã do portal do Apple School Manager com a opção Número de Série selecionada](./media/asm-server-assignment.png)

4.  Selecione **Carregar Ficheiro...** no portal da Apple, procure o ficheiro .pem e selecione **Guardar Servidor MDM** (canto inferior direito).
5.  Selecione **Obter Token** e, em seguida, transfira o ficheiro do token do servidor (.p7m) para o computador.
6. Vá para **Atribuições de Dispositivo** e **Escolher Dispositivo** através da introdução manual dos **Números de Série**, **Número do Pedido** ou **Carregar Ficheiro CSV**.
     ![Captura de ecrã do portal do Apple School Manager com a opção Número de Série selecionada](./media/asm-device-assignment.png)
7.  Selecione a ação **Atribuir ao Servidor** e selecione o **Servidor MDM** que criou.
8. Especifique como irá **Escolher Dispositivos** e, em seguida, forneça as informações e detalhes do dispositivo.
9. Selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, selecione **OK**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passo 3: Guardar o Apple ID que serviu para criar este token

No Intune no portal do Azure, forneça o ID Apple para referência futura.

![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Passo 4: Carregar o token
Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune sincroniza automaticamente os seus dispositivos Apple School Manager da Apple.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple
Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos Apple School. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token, escolha **Perfis** e, em seguida, escolha **Criar perfil**.

3. Em **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade do Utilizador** – escolha esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar o portal da empresa para serviços como a instalação de aplicações. Esta opção também permite que os utilizadores autentiquem os respetivos dispositivos através do portal da empresa. Se estiver a utilizar o Sistema de Ficheiros Distribuído do Azure, a afinidade de utilizador precisa de um [Nome de utilizador/Ponto final misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   O modo iPad Partilhado do Apple School Manager exige que o utilizador se inscreva sem a afinidade de utilizador.

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não afiliados a um único utilizador, como um dispositivo partilhado. Utilize esta opção para dispositivos que realizem tarefas sem aceder aos dados de utilizador locais. As aplicações, como o Portal da Empresa, não funcionam.

5. Se tiver escolhido **Inscrever com Afinidade do Utilizador**, tem a opção para permitir que os utilizadores se autentiquem com o Portal da Empresa em vez do Assistente de Configuração da Apple.

    ![Autentique com o Portal da Empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se quiser realizar alguma das seguintes ações, defina **Autenticar com o Portal da Empresa em vez do Assistente de Configuração da Apple** para **Sim**.
    >    - utilizar a autenticação multifator
    >    - pedir aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez
    >    - Pedir aos utilizadores para reporem as respetivas palavras-passe expiradas durante a inscrição
    >
    > Estas ações não são suportadas durante a autenticação com o Assistente de Configuração da Apple.

6. Escolha **Definições de Gestão de Dispositivos** e selecione se quer ou não que os dispositivos com este perfil sejam supervisionados.
    Os dispositivos **supervisionados** proporcionam mais opções de gestão e desativam o Bloqueio de Ativação por predefinição. A Microsoft recomenda a utilização do DEP como o mecanismo para ativar o modo supervisionado, especialmente para as organizações que estiverem a implementar um grande número de dispositivos iOS.

    Os utilizadores são notificados de que os seus dispositivos são supervisionados de duas formas:

   - O ecrã de bloqueio indica: "Este iPhone é gerido pela Contoso."
   - O **configurações** > **geral** > **sobre** ecrã diz: "Este iPhone é supervisionado. A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo."

     > [!NOTE]
     > Um dispositivo inscrito sem supervisão só pode ser reposto para supervisionado com o Apple Configurator. Repor o dispositivo desta forma requer ligar um dispositivo iOS a um Mac com um cabo USB. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Escolha se quer ou não a inscrição bloqueada para dispositivos com este perfil. A **Inscrição bloqueada** desativa as definições do iOS que permitem que o perfil de gestão seja removido do menu **Definições**. Após a inscrição de dispositivos, não poderá alterar esta definição sem apagar os dados do dispositivo. Esses dispositivos têm de ter o Modo de Gestão **Supervisionado** definido como *Sim*. 

8. Se quiser permitir que vários utilizadores iniciem sessão em iPads inscritos com um Apple ID gerido, escolha **Sim** em **iPad Partilhado** (esta opção exige que **Inscrever com Afinidade de Utilizador**e o modo **Supervisionado** esteja definido como **Sim**.) Os Apple IDs geridos são criados no portal do Apple School Manager. Saiba mais sobre [iPad partilhado](education-settings-configure-ios-shared.md) e [requisitos dos iPad partilhados da Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Escolha se quer ou não que os dispositivos com este perfil consigam **Sincronizar com computadores**. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

10. Se tiver escolhido **Permitir o Apple Configurator por certificado** no passo anterior, escolha um Certificado do Apple Configurator a importar.

11. Escolha **OK**.

12. Selecione **Definições do Assistente de Configuração** para configurar as seguintes definições de perfil: ![Personalização do Assistente de configuração.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Definição                  |                                                                                               Descrição                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Nome do Departamento</strong>     |                                                             É apresentado quando os utilizadores tocam em <strong>Acerca da Configuração</strong> durante a ativação.                                                              |
    |    <strong>Número de Telefone do Departamento</strong>     |                                                          Aparece quando o utilizador clica no botão <strong>Preciso de Ajuda</strong> durante a ativação.                                                          |
    | <strong>Opções do Assistente de Configuração</strong> |                                                     As seguintes definições opcionais podem ser configuradas posteriormente no menu <strong>Definições</strong> do iOS.                                                      |
    |        <strong>Código de Acesso</strong>         | Pedido de código de acesso durante a ativação. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação). |
    |    <strong>Serviços de Localização</strong>    |                                                                 Se ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                  |
    |         <strong>Restaurar</strong>         |                                                                Se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação.                                                                 |
    |   <strong>iCloud e Apple ID</strong>   |                         Se estiver ativado, o Assistente de Configuração solicita ao utilizador que inicie sessão com um Apple ID e o ecrã de Aplicações e Dados irá permitir que o dispositivo seja restaurado a partir da cópia de segurança de iCloud.                         |
    |  <strong>Termos e Condições</strong>   |                                                   Se estiver ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Se estiver ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Se estiver ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                 |
    |          <strong>Zoom</strong>           |                                                                 Se estiver ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Se estiver ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                 |
    |     <strong>Dados de Diagnóstico</strong>     |                                                                 Se estiver ativado, o Assistente de Configuração solicita este serviço durante a ativação.                                                                 |


13. Escolha **OK**.

14. Para guardar o perfil, escolha **Criar**.

## <a name="connect-school-data-sync"></a>Ligar a Sincronização de Dados da Escola
(Opcional) O Apple School Manager suporta a sincronização de dados da lista de participantes para o Azure Active Directory (AD) ao utilizar o Microsoft School Data Sync (SDS). Apenas pode sincronizar um token com o SDS. Se configurar outro token com o School Data Sync, o SDS será removido do token que o tinha anteriormente. Uma nova ligação substituirá o token atual. Conclua os seguintes passos para utilizar SDS para sincronizar os dados da escola.

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token do Apple School Manager e, em seguida, escolha o **School Data Sync**.
3. Em **School Data Sync**, escolha **Permitir**. Esta configuração permite que o Intune se ligue à SDS no Office 365.
4. Para ativar uma ligação entre o Apple School Manager e o Azure AD, selecione **Configurar o Microsoft School Data Sync**. Saiba mais sobre [como configurar a Sincronização de Dados da Escola](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Clique em **Guardar** > **OK**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos

Depois de atribuída a permissão ao Intune para gerir os dispositivos associados ao Apple School Manager, sincronize o Intune com o serviço Apple para ver os dispositivos geridos no Intune.

No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista > **Dispositivos** > **Sincronizar**. ![Captura de ecrã a mostrar o nó Dispositivos do Programa de Inscrição selecionado e a opção Sincronizar ligação a ser selecionada.](./media/device-enrollment-program-enroll-ios/image06.png)

  Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
  - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza todos os números de série da Apple atribuídos ao Intune. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
  - São atribuídos 15 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.
  - O Intune sincroniza os dispositivos novos e removidos com a Apple a cada 24 horas.

>[!NOTE]
>Também pode atribuir números de série do Apple School Manager aos perfis do painel **Programa de Inscrição de Dispositivos**.

## <a name="assign-a-profile-to-devices"></a>Atribuir um perfil a dispositivos
É necessário atribuir um perfil do programa de inscrição aos dispositivos associados ao Apple School Manager geridos pelo Intune antes de estes serem inscritos.

1. No [Intune](https://aka.ms/intuneportal), escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos e, em seguida, escolha **Atribuir**.

## <a name="distribute-devices-to-users"></a>Distribuir dispositivos pelos utilizadores

Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a inscrição dos seus dispositivos Apple School. Agora pode distribuir os dispositivos aos utilizadores. Quando um dispositivo iOS associado ao Apple School Manager é ligado, é inscrito na gestão pelo Intune. Se o dispositivo foi ativado e estiver a ser utilizado, não poderá aplicar o perfil até o dispositivo ser apagado.
