---
title: Inscrever dispositivos iOS – Programa de Registo de Aparelho
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos iOS pertencentes à empresa através do Programa de Registo de Aparelho (nova IU).
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5532e00f90702b820ec5bed6bf2fdb3d5e9d37df
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscrever automaticamente dispositivos iOS com o Programa de Inscrição de Dispositivos da Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Diferenças na interface de utilizador temporárias
> As interfaces de utilizador para as funcionalidades descritas nesta página estão a ser atualizadas. Estas atualizações estão a ser implementadas em todas as contas de utilizador até ao fim de abril.
>
> Se a página **Inscrição de dispositivos** tiver um aspeto semelhante à imagem abaixo, tem as interfaces de utilizador atualizadas e pode utilizar esta página de ajuda.
>
> ![Nova interface de utilizador](./media/appleenroll-newui.png)
>
> Caso contrário, se a página **Inscrição de dispositivos** tiver um aspeto semelhante à imagem abaixo, a sua conta ainda não foi atualizada para a nova interface de utilizador. Aceda a [esta página de ajuda](device-enrollment-program-enroll-ios.md).
>
> ![Interface de utilizador antiga](./media/appleenroll-oldui.png)

Este tópico ajuda-o a ativar a inscrição de dispositivos iOS para dispositivos adquiridos através do [Programa de Inscrição de Dispositivos (DEP)](https://deploy.apple.com) da Apple. Pode ativar a inscrição de DEP para um grande número de dispositivos de forma remota. Pode enviar dispositivos, como iPhones e iPads, diretamente aos utilizadores. Quando o utilizador ativar o dispositivo, o Assistente de Configuração será executado com as predefinições configuradas e o dispositivo será inscrito na gestão.

Para ativar a inscrição DEP, deve utilizar os portais do Intune e do Apple DEP. É necessária uma lista de números de série ou um número de encomenda para poder atribuir dispositivos ao Intune para gestão. São criados os perfis de inscrição DEP com as definições aplicadas aos dispositivos durante a inscrição.

A propósito, a inscrição DEP não funciona com o [gestor de inscrição de dispositivos](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>O que é o modo supervisionado?
A Apple incluiu o modo supervisionado pela primeira vez no iOS 5. Um dispositivo iOS no modo supervisionado pode ser gerido com mais controlos. Como tal, é especialmente útil para dispositivos pertencentes à empresa. Como parte do Programa de Inscrição de Dispositivos Apple (DEP), o Intune suporta a configuração de dispositivos para o modo supervisionado. 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Pré-requisitos
- Dispositivos adquiridos através do [Programa de Inscrição de Dispositivos da Apple](http://deploy.apple.com)
- [Autoridade MDM](mdm-authority-set.md)
- [Certificado Push de MDM da Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obter um token DEP da Apple

Antes de poder inscrever dispositivos iOS com DEP, precisa de um ficheiro token DEP (.p7m) da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos DEP que são propriedade da sua empresa. Também permite ao Intune carregar perfis de inscrição para a Apple e atribuir dispositivos a esses perfis.

Pode utilizar o portal de DEP da Apple para criar um token DEP. Também pode utilizar o portal de DEP para atribuir dispositivos ao Intune para gestão.

> [!NOTE]
> Se eliminar o token do portal clássico do Intune antes da migração para o Azure, o Intune poderá restaurar um token DEP da Apple eliminado. Pode eliminar novamente o token DEP do portal do Azure. Pode eliminar novamente o token DEP do portal do Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passo 1: Transfira o certificado de chave pública do Intune, que é obrigatório para criar o token.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do Programa de Inscrição** > **Adicionar**.

    ![Obtenha um token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Conceda permissão à Microsoft para enviar informações sobre o utilizador e o dispositivo à Apple, ao selecionar **Concordo**.

   ![Captura de ecrã a mostrar o painel Token do Programa de Inscrição, na área de trabalho Certificados da Apple, para transferir a chave pública.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Selecione **Transferir a chave pública** para transferir e guardar o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passo 2: Utilize a sua chave para transferir um token a partir da Apple.

1. Selecione **Criar um token para o Programa de Registo de Aparelho da Apple** para abrir o portal Programa de Implementação da Apple e inicie sessão com o Apple ID da sua empresa. Pode utilizar este Apple ID para renovar o seu token DEP.
2.  No [portal dos Programas de Implementação](https://deploy.apple.com) da Apple, selecione **Começar** em **Programa de Registo de Aparelho**.

3. Na página **Gerir Servidores**, selecione **Adicionar Servidor MDM**.
4. Introduza o **Nome do Servidor MDM** e, em seguida, selecione **Seguinte**. O nome do servidor é uma referência para identificar o servidor de gestão de dispositivos móveis (MDM). Não é o nome nem o URL do Microsoft Intune.

5. A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** é aberta e pede para **Atualizar a Chave Pública**. Selecione **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, selecione **Seguinte**.

6. Aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**.
7. Em **Selecionar Dispositivos Por**, especifique a forma como os dispositivos são identificados:
    - **Número de Série**
    - **Número da Encomenda**
    - **Carregar Ficheiro CSV**.

   ![Captura de ecrã a mostrar a especificação de dispositivos selecionados pelo número de série, a definição da ação de seleção como Atribuir ao servidor e a seleção do nome do servidor.](./media/enrollment-program-token-specify-serial.png)

8. Em **Selecionar Ação**, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado no Microsoft Intune e, em seguida, selecione **OK**. O portal da Apple atribui os dispositivos especificados para o servidor do Intune para gestão e, em seguida, apresenta a mensagem **Atribuição Concluída**.

   No portal da Apple, aceda a **Programas de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Ver Histórico de Atribuições** para ver uma lista de dispositivos e a respetiva atribuição de servidores MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passo 3: Guarde o Apple ID que serviu para criar este token.

No Intune no portal do Azure, forneça o ID Apple para referência futura.

![Captura de ecrã a mostrar a especificação do ID Apple utilizado para criar o token do programa de inscrição e o acesso ao token do programa de inscrição.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Passo 4: Carregue o seu token.
Na caixa **Token da Apple**, procure o ficheiro de certificado (.pem), escolha **Abrir** e, em seguida, escolha **Criar**. Com o certificado push, o Intune pode inscrever e gerir dispositivos iOS ao enviar políticas para dispositivos móveis inscritos. O Intune é sincronizado automaticamente na Apple para que possa ver a conta do seu programa de inscrição.

## <a name="create-an-apple-enrollment-profile"></a>Criar um perfil de inscrição da Apple

Agora que instalou o seu token, pode criar um perfil de inscrição para dispositivos DEP. Um perfil de inscrição de dispositivos especifica as definições aplicadas a um grupo de dispositivos durante a inscrição.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição**.
2. Selecione um token, escolha **Perfis** e, em seguida, escolha **Criar perfil**.
    ![Crie uma captura de ecrã do perfil.](./media/device-enrollment-program-enroll-ios/image04.png)
3. Em **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil para efeitos administrativos. Os utilizadores não verão estes detalhes. Pode utilizar este campo **Nome** para criar um grupo dinâmico no Azure Active Directory. Utilize o nome de perfil para definir o parâmetro enrollmentProfileName para atribuir dispositivos com este perfil de inscrição. Saiba mais sobre os [grupos dinâmicos do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Nome do perfil e descrição.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Na **Afinidade do Utilizador**, escolha se os dispositivos com este perfil têm de ser inscritos com ou sem um utilizador atribuído.
    - **Inscrever com Afinidade do Utilizador** – escolha esta opção para os dispositivos que pertençam aos utilizadores e que queiram utilizar o portal da empresa para serviços como a instalação de aplicações. Esta opção também permite que os utilizadores autentiquem os respetivos dispositivos através do portal da empresa. A afinidade do utilizador necessita do [WS-Trust 1.3 Username/Mixed endpoint](https://technet.microsoft.com/library/adfs2-help-endpoints). [Saiba mais](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscrever sem Afinidade do Utilizador** – escolha esta opção para dispositivos não associados a um único utilizador. Utilize esta opção para dispositivos que realizem tarefas sem aceder aos dados de utilizador locais. As aplicações, como o Portal da Empresa, não funcionam.

5. Se tiver escolhido **Inscrever com Afinidade do Utilizador**, tem a opção para permitir que os utilizadores se autentiquem com o Portal da Empresa em vez do Assistente de Configuração da Apple.

    ![Autentique com o Portal da Empresa.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > A Autenticação multifator (MFA) não funciona durante a inscrição de DEP se tiver as propriedades do perfil definidas como **Inscrever com Afinidade do Utilizador** e não estiver a utilizar um Portal da Empresa. Depois da inscrição, a MFA funciona conforme esperado nos dispositivos. Os dispositivos não pedem aos utilizadores para alterar a palavra-passe ao iniciar sessão pela primeira vez. Além disso, não é pedido aos utilizadores com palavras-passes expiradas que reponham a palavra-passe durante a inscrição. Os utilizadores terão de repor a palavra-passe a partir de um dispositivo diferente.

6. Escolha **Definições de Gestão de Dispositivos** e selecione se quer ou não que os dispositivos com este perfil sejam supervisionados.
    Os dispositivos **supervisionados** proporcionam mais opções de gestão e desativam o Bloqueio de Ativação por predefinição. A Microsoft recomenda a utilização do DEP como o mecanismo para ativar o modo supervisionado, especialmente para as organizações que estiverem a implementar um grande número de dispositivos iOS.

    Os utilizadores são notificados de que os seus dispositivos são supervisionados de duas formas:

   - O ecrã de bloqueio indica: "Este iPhone é gerido pelo Contoso."
   - O ecrã **Definições** > **Geral** > **Acerca de** indica: "Este iPhone é supervisionado. A Contoso consegue monitorizar o seu tráfego de Internet e localizar este dispositivo."

     > [!NOTE]
     > Um dispositivo inscrito sem supervisão só pode ser reposto para supervisionado com o Apple Configurator. Repor o dispositivo desta forma requer ligar um dispositivo iOS a um Mac com um cabo USB. Saiba mais sobre este assunto nos [documentos do Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Escolha se quer ou não a inscrição bloqueada para dispositivos com este perfil. A **Inscrição bloqueada** desativa as definições do iOS que permitem que o perfil de gestão seja removido do menu **Definições**. Após a inscrição de dispositivos, não poderá alterar esta definição sem efetuar uma reposição de fábrica do dispositivo. Esses dispositivos têm de ter o Modo de Gestão **Supervisionado** definido como *Sim*. 

8. Escolha se quer ou não que os dispositivos com este perfil consigam **Sincronizar com computadores**. Se escolher **Permitir o Apple Configurator por certificado**, terá de escolher um certificado em **Certificados do Apple Configurator**.

9. Se tiver escolhido **Permitir o Apple Configurator por certificado** no passo anterior, escolha um Certificado do Apple Configurator a importar.

10. Escolha **OK**.

11. Escolha **Definições do Assistente de Configuração** para configurar as seguintes definições de perfil: ![Personalização do Assistente de Configuração.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


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


12. Escolha **OK**.

13. Para guardar o perfil, escolha **Criar**.

## <a name="sync-managed-devices"></a>Sincronizar dispositivos geridos
Agora que o Intune tem permissão para gerir os seus dispositivos, pode sincronizar o Intune com a Apple para ver os seus dispositivos geridos no Intune no portal do Azure.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos** > **Inscrição da Apple** > **Tokens do programa de inscrição** > escolha um token na lista > **Dispositivos** > **Sincronizar**. ![Captura de ecrã a mostrar o nó Dispositivos do Programa de Inscrição selecionado e a opção Sincronizar ligação a ser selecionada.](./media/device-enrollment-program-enroll-ios/image06.png)

   Para cumprir os termos da Apple para um tráfego aceitável do programa de inscrição, o Intune impõe as seguintes restrições:
   - As sincronizações completas não podem ser executadas mais do que uma vez a cada sete dias. Durante uma sincronização completa, o Intune atualiza todos os números de série da Apple atribuídos ao Intune. Se for tentada uma sincronização completa no prazo de sete dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
   - São atribuídos 15 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão **Sync (Sincronizar)** está desativado.
   - O Intune sincroniza os dispositivos novos e removidos com a Apple a cada 24 horas.

## <a name="assign-an-enrollment-profile-to-devices"></a>Atribuir um perfil de inscrição a dispositivos
Tem de atribuir um perfil do programa de inscrição aos dispositivos para poder inscrevê-los.

>[!NOTE]
>Também pode atribuir números de série a perfis a partir do painel **Números de Série da Apple**.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos**  >  **Inscrição da Apple**  >  **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Dispositivos** > escolha dispositivos na lista > **Atribuir perfil**.
3. Em **Atribuir perfil**, escolha um perfil para os dispositivos e, em seguida, escolha **Atribuir**.

### <a name="assign-a-default-profile"></a>Atribuir um perfil predefinido

Pode escolher um perfil predefinido a aplicar a todos os dispositivos que inscrever com um token específico.

1. No Intune no portal do Azure, escolha **Inscrição de dispositivos**  >  **Inscrição da Apple**  >  **Tokens do programa de inscrição** > escolha um token na lista.
2. Escolha **Definir o Perfil Predefinido**, escolha um perfil na lista pendente e, em seguida, escolha **Guardar**. Este perfil será aplicado a todos os dispositivos inscritos com o token.

## <a name="distribute-devices"></a>Distribuir dispositivos
Ativou a gestão e sincronização entre a Apple e o Intune e atribuiu um perfil para permitir a inscrição dos seus dispositivos DEP. Agora pode distribuir os dispositivos aos utilizadores. Os dispositivos com afinidade do utilizador necessitam que seja atribuída uma licença do Intune a cada utilizador. Os dispositivos sem afinidade do utilizador necessitam de uma licença de dispositivo. Um dispositivo ativado não poderá aplicar um perfil de inscrição até que seja realizada uma reposição de fábrica do dispositivo.

Veja [Inscrever o dispositivo iOS no Intune com o Programa de Registo de Aparelho](/intune-user-help/enroll-your-device-dep-ios).


